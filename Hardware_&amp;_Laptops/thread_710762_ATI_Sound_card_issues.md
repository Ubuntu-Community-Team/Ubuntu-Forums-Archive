---
title: "ATI Sound card issues"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by drinkymilk on 2008-02-28
Ok so I have scoured the web for answers and so far I haven't been able to come up with anything. In fact I was really hoping I didn't have to resort to posting a new question. But you know what they say : the man who asks the question is a fool for five minutes, the man who does not ask the questions is a fool forever.

So heres my problem. I am running an eMachine with an onboard ATI IXP sound card. I haven't had any problems with it until the other night when it simply stopped working altogether. the only thing I did differently is that I set power management to put my computer to sleep after one hour of inactivity. after it went to sleep I haven't had any sound. I tried restarting, and the sound doesn't even come on for ubuntu log in thingy. I'm not sure what to do or where to go. A few more things to note I am using Ubuntu 7.10 Gutsy, and I listen to alot of music :( . I really hope I can resolve this soon, as I will -never- be resorting back to windows.

~tim

---

### Post by Yellow Pasque on 2008-02-28
Is it high-def audio or regular AC97? (use *sudo lshw -C multimedia* if unsure)

---

### Post by drinkymilk on 2008-02-28
regular AC97

---

### Post by superprash2003 on 2008-02-29
try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by drinkymilk on 2008-02-29
Yeah I tried that a long time ago:confused:

---

### Post by Yellow Pasque on 2008-02-29
> **superprash2003 said:**
> try this..may work [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)
Are you really trying to solve people's sound problems or are you just pasting that little tid-bit in every sound thread to promote your blog?

---

### Post by Yellow Pasque on 2008-02-29
> **Temüjin said:**
> Are you really trying to solve people's sound problems or are you just pasting that little tid-bit in every sound thread to promote your blog?
drinky,
I'd really like to solve your problem. I might have you try using OSS4, but first let's try upgrading to the latest ALSA (script attached to post).

```
sudo chmod 777 alsa_1.sh
sudo sh ./alsa_1.sh
```

---

### Post by drinkymilk on 2008-02-29
ok well I updated the alsa driver like you told me to but the code:
sudo chmod 777 alsa_1.sh
didn't seem to do any thing.

but of course the code 
sudo sh ./alsa_1.sh
did a whole alot of stuff.
still no sound maybe i'll try restarting...

---

### Post by drinkymilk on 2008-02-29
> **drinkymilk said:**
> ok well I updated the alsa driver like you told me to but the code:
sudo chmod 777 alsa_1.sh
didn't seem to do any thing.

but of course the code 
sudo sh ./alsa_1.sh
did a whole alot of stuff.
still no sound maybe i'll try restarting...

yup restart didn't do anything, kinda not very surprised...

i tried this code just now:
sudo chmod -v 777 /home/tim/Desktop/alsa_1.sh

with this result:
mode of `/home/tim/Desktop/alsa_1.sh' retained as 0777 (rwxrwxrwx)

hope that helps with something, because I am still lost...

---

### Post by drinkymilk on 2008-03-01
> **drinkymilk said:**
> yup restart didn't do anything, kinda not very surprised...

i tried this code just now:
sudo chmod -v 777 /home/tim/Desktop/alsa_1.sh

with this result:
mode of `/home/tim/Desktop/alsa_1.sh' retained as 0777 (rwxrwxrwx)

hope that helps with something, because I am still lost...


Yeah so I went ahead and just followed directs you gave for OSS4 and that worked like a charm. thanks for very comprehensive and completely understandable directions, and totally fast install. 

awesome the music is back!:guitar:

thanks again

~tim

---

