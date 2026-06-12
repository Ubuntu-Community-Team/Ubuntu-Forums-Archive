---
title: "No WiFi at all - ACER  TravelMate 5320 Ubuntu 12.04"
date: 2012-05-02
forum: Hardware
---

### Post by koosfoto.hu on 2012-05-02
Greetings!

I have just installed the new Ubuntu 12.04 on my Acer TravelMate 5320.
It was easy and quick! THANKS.

The thing is, that there is no WiFi at all... it does not detect any of the available wireless networks. 

What can be done? How to connect to the internet?

Thanks a lot,

Tamas

---

### Post by Pioden on 2012-08-02
Did you find an answer Tamas? I have the same problem. Drivers say their installed but I cannot get wifi to switch on. Strange.

---

### Post by koosfoto.hu on 2012-08-02
Hi Pioden!
Yes, it works fine now! I love it.
Well, a friend of mine came over and made it work... However, I have no idea what did he do to make it happen.
If you want me to, I can ask him... 

Greetings,

T.

---

### Post by Pioden on 2012-08-02
That would be good :-) I have tried many things but no luck so far.

---

### Post by koosfoto.hu on 2012-08-05
Hi, Pioden!

I am sorry... my friend does not remember what he has done with my Ubuntu... and he, who used to love Ubuntu... now says, he would not write anymore on the forum... as there things in the rules he cannot accept. :(

And only he knows my Ubuntu well enough... 

So, I am really sorry... I cannot help you out. :(

Good luck and greetings,

T.

---

### Post by mariaque on 2012-09-15
Hi Pioden,

were you able to find a solution? I have exactly the same problem on the same computer. Also, if you have a solution, could you please explain it to  me in a very simple manner? I am really not confident with the terminal. Thank you,
M

---

### Post by mariaque on 2012-09-16
Pioden!!

I found something that worked for me! I'm not an expert but it seemed to be a driver problem. If your computer uses Broadcom go to [http://linuxwireless.org/en/users/Drivers/b43#supported](http://linuxwireless.org/en/users/Drivers/b43#supported)

I hope it'll also work for you. 

For any expert reading this, I have one last problem. I have to go to the terminal EVERY time I log on and write
sudo modprobe b43

Is there a way for ,y computer to connect to the wireless automatically?
Again, I am not a programmer so simple answers are very much appreciated. Thank you

---

### Post by varunendra on 2012-09-18
> **mariaque said:**
> I have to go to the terminal EVERY time I log on and write
sudo modprobe b43
Is there a way for ,y computer to connect to the wireless automatically?
This should work-
Open terminal, type (or better, copy-paste) and enter this:
```
echo "b43" | sudo tee -a /etc/modules
```

**Description: **the above command will add a line "b43" (without quotes) in your /etc/modules file. The modules added to this file are automatically loaded at startup.

***PS:***
Generally the b43 module does not need additional tinkering as above if it is installed correctly. So I doubt if you installed it correctly. Take a look at this post to see the correct method: [http://ubuntuforums.org/showpost.php?p=11403088](http://ubuntuforums.org/showpost.php?p=11403088)

---

### Post by felipeperucho on 2013-01-19
¡Worked for me! "sudo apt-get install firmware-b43-installer" made the magic on Ubuntu 12.04 :)

---

