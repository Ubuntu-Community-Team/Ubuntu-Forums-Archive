---
title: "Help with http://www.kyz.uklinux.net/cabextract.php"
date: 2008-07-31
forum: Hardware
---

### Post by Blackdude on 2008-07-31
Hey, 

I'm new and i am dutch so don't look at my english.
I want to install [http://www.kyz.uklinux.net/cabextract.php](http://www.kyz.uklinux.net/cabextract.php) on my pc but it's forbidde.. It's for to run schockwave.. 
The say that i need to install it but where can i do that?

Greetingss Danny:popcorn:

---

### Post by lordadi on 2008-07-31
Hi,

In a terminal (Applications > Accessories > Terminal) type:
```
sudo apt-get install cabextract
```


This will download and install cabextract on your computer,


Cheers,


Lordadi.

---

### Post by madarcher on 2008-07-31
```
sudo apt-get install cabextract
```

This should sort you out

---

### Post by Blackdude on 2008-07-31
> **lordadi said:**
> Hi,

In a terminal (Applications > Accessories > Terminal) type:
```
sudo apt-get install cabextract
```


This will download and install cabextract on your computer,


Cheers,


Lordadi.

Thankss man, But i realy don't now my sudo password..

What to do??

---

### Post by lordadi on 2008-07-31
Hi,


Reboot your computer and at grub select recovery console. It will take you to a terminal over there, type: ```
sudo passwd <your username>
``` or maybe even ```
passwd <your  username>
```

I do not think that it will ask for sudo passwd. If it does not work, just search the forums for "Help I forgot my password" or something similar :D

Also, you will not see the password being entered or any asterisks or anything. However, your password is being accepted.

Cheers,


Lordadi.

---

### Post by madarcher on 2008-07-31
If you are the only user on the machine, your sudo password should be the same as your user password.

John

---

### Post by lordadi on 2008-07-31
I dint think of that!! Yup that should work too.

---

### Post by Blackdude on 2008-07-31
> **lordadi said:**
> I dint think of that!! Yup that should work too.

Thxx boys i got it :guitar:

---

### Post by lordadi on 2008-07-31
Glad to hear it worked.

Which one was it? sudo passwd or passwd?


Cheers,


Lordadi.

---

### Post by Blackdude on 2008-07-31
> **lordadi said:**
> Glad to hear it worked.

Which one was it? sudo passwd or passwd?


Cheers,


Lordadi.

Just enter. But nou i have microsoft internet explore 6.0 on ubunto and i instalt shockwave ans al. But i want to play habbo.nl but i says that my shockwave is not compatebile with my operating systeem...

---

### Post by lordadi on 2008-07-31
Hi,


I don't know, habbo.nl worked for me (didn't understand what was going on but that's a different story). Maybe you should try to get your Flash from Adobe's site? [Flash @ Adobe]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash"). Select the .tar.gz for Linux. Download somewhere and decompress it. Inside the folder, double click the flash installer and then "run in terminal", answer the questions and it will install it for you.

Try habbo.nl after this.

Cheers,


Lordadi.
P.S: You use Firefox right?

---

### Post by Blackdude on 2008-08-03
> **lordadi said:**
> Hi,


I don't know, habbo.nl worked for me (didn't understand what was going on but that's a different story). Maybe you should try to get your Flash from Adobe's site? [Flash @ Adobe]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash"). Select the .tar.gz for Linux. Download somewhere and decompress it. Inside the folder, double click the flash installer and then "run in terminal", answer the questions and it will install it for you.

Try habbo.nl after this.

Cheers,


Lordadi.
P.S: You use Firefox right?

Hi,

It realy doesn't work.. I try'd evertything what you say. 
It says that i need to instal shockwave 11 for my systeem. I tryt Internet explorer and instalt Shockwave 11 for explorer but it's says again that is nog for my systeem.. what to do??

Gr Blackdude.

---

### Post by lordadi on 2008-08-05
Hi,

If you have IE working under wine, then you should be able to play habbo.nl by doing this:
[LIST=1]
[*]Install the Windows Firefox or IE (you've already done this)
[*]Go to [Shockwave @ Adobe]("http://www.adobe.com/shockwave/download/alternates/#sp")and download the windows Shockwave player (for FF or IE)
[*]Restart your windows FF/IE
[/LIST]
It should now work.:)


Cheers, 


Lordadi.

---

### Post by highhippyfun on 2009-02-02
> **lordadi said:**
> hi,

in a terminal (applications > accessories > terminal) type:
```
sudo apt-get install cabextract
```


this will download and install cabextract on your computer,


cheers,


lordadi.

omg dude you helped me so much thanks!!!!!!

---

### Post by lordadi on 2009-02-02
No problem!

---

