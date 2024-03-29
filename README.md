# UDP server-client model

Документація до ТЗ.

## Опис програми

При натисканні на кнопку "Click!", програма надсилає масив з мільйона даблів (за замовчуванням). Вище, над кнопкою, є рядок, куди можна написати бажану кількість елементів у масиві. Щоб надіслати їх знову, просто потрібно натиснути на кнопку "Click!" ще раз.

### Опис логіки вводу

Лінія утворена таким чином, що туди можна записувати лише числа, які більше нуля. Якщо ви вже написали яке-небудь число, наприклад, 1000, і потім захочете надіслати 99999, то при спробі видалити 1000, ви не зможете видалити саму першу цифру (так при будь-якому числі). Щоб вирішити цю проблему, потрібно буде:
1. Залишити 2 цифри         (1000 -> 1 -> 19 (9, цифра нового числа)) 
2. Натискати клавішу "<-"    
3. Видалити першу цифру     (19 -> 9)
4. Далі пишіть своє число  

### Файл конфігурації

У файлі "config.ini" можна змінити номери портів та локальну адресу. Також можна додати ще один порт або видалити один (за замовчуванням встановлено 2 порти). Максимальна кількість приймаючих портів - 3.
Щоб додати його, потрібно написати "Port" + наступний індекс порту (з нуля). Програма автоматично створить новий потік.

### Запис даних

Дані записуються у бінарний файл. Для кожного потоку генерується свій файл. Якщо ви закриєте програму і при цьому не видалите файл (або не зміните), нові дані додаються до старих файлів.

### Багатопотоковість

Програма використовує багатопотоковість. Сервер надсилає дані з основного потоку, клієнти приймають у різних. Для того щоб клієнти встигали приймати дані, основний потік сповільнюється на частку мілісекунди.

