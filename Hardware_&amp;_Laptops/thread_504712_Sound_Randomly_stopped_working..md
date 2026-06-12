---
title: "Sound Randomly stopped working."
date: 2007-07-19
forum: Hardware &amp; Laptops
---

### Post by rohizzle121 on 2007-07-19
i am total newb [4 days total]  at linux. i just got festsy fawn not to long ago [3 days]. When i first installed fawn is was working perfectly,  but all of a sudden it stopped working. yesterday i tried to install "complz" [still no luck =[ lol] and after i rebooted and now its not working. what should i do?

---

### Post by sunshine12 on 2007-07-19
May be due to feisty randomly selecting your soundcard from the soundcard list...

just type this in terminal.. (To bring Terminal press Alt+F2, write gnome-terminal, hit enter)

sudo asoundconf list

then select which is your sound card..

sudo asoundconf set-default-card YOUR-CARD-NAME

this will choose the selected sound card as default..

---

### Post by rohizzle121 on 2007-07-19
i tried that with both sound cards that i have listed and it still doesnt work. i went in to sounds >preferences  and i played the noise for log out and log in and i went to youtube and played a video. still no sound =[. is there anything i can try?

---

