---
title: "kensington expert mouse button mapping"
date: 2013-12-24
forum: Hardware
---

### Post by mrkaplan on 2013-12-24
i have been trying to get xinput to work at startup  with no luck . 
right now in startup apps i have the following code
"xinput set-button-map `xinput list | grep 'Kensington      Kensington Expert Mouse' | grep -o [0-9][0-9]` 8 1 1 3 4 5 6 7 8 9 10 11 12" 
which does nothing  .  
i can of course manually copy and paste the xinput cmd in the terminal for each session : which works .  but id like a permanent solution .
thanks for any help.

---

### Post by mrkaplan on 2013-12-25
figured it out . for other new users interested heres what to do
open terminal , type xinput list 
copy entire device name exactly as it is 
then go to startup applications, add 
in command field ,type :  xinput set-button-map "<paste device name>"
(note the quotes) 
could not get it to work with device id , but this does it for me

---

