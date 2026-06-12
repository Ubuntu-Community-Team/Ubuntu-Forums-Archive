---
title: "how to install gmabooster"
date: 2009-06-23
forum: Installation &amp; Upgrades
---

### Post by rajanm1 on 2009-06-23
how can i install gma booster for my mini 9 with ubantu 8.04lts from here [http://www.gmabooster.com/download.htm](http://www.gmabooster.com/download.htm) ??

thanks

---

### Post by Mark Phelps on 2009-06-23
It says to launch the program in a terminal and follow the on-screen instructions. Other than doing Applications --> Accessories --> Terminal to launch a terminal, and then "sudo -i" to login as root, you need to follow their instructions.

If you have specific questions about parts of their instructions, you need to provide the details.

---

### Post by rajanm1 on 2009-06-24
> **Mark Phelps said:**
> It says to launch the program in a terminal and follow the on-screen instructions. Other than doing Applications --> Accessories --> Terminal to launch a terminal, and then "sudo -i" to login as root, you need to follow their instructions.

If you have specific questions about parts of their instructions, you need to provide the details.
 
i am new to linux but followed their instructions and couldn't get it to install.
i downloaded it and then typed in "sudo -i" to login as root and then when i right click it all it says it do i want to run with autoprompt, so i click that but nothing happens :-s.
could you please give me step by step instructions of how to install it please? (i'm not an idiot really, just new to this whole new linux way)

thanks

---

### Post by Mark Phelps on 2009-06-25
Sorry, but the only way for me to read the instructions is to launch the installer -- and I'm not going to risk damaging my system by installing this, especially since I do NOT have an intel GMA chip.

---

### Post by rajanm1 on 2009-06-26
> **Mark Phelps said:**
> Sorry, but the only way for me to read the instructions is to launch the installer -- and I'm not going to risk damaging my system by installing this, especially since I do NOT have an intel GMA chip.

how do you launch the installer? it doesn't do that automatically for me and when i right click it is not in the options

---

### Post by rajanm1 on 2009-07-04
bump

---

### Post by aperture123 on 2009-07-08
> **rajanm1 said:**
> how do you launch the installer? it doesn't do that automatically for me and when i right click it is not in the options

I think what he means is that you have to launch through root user, and not by right clicking it. You need to run it through the terminal. The fact that it isn't installed into the system makes it harder. 
Since the file only has GMABooster, the readme, and the data.bin, I am not sure how to tackle this.
I have very little experiance with Ubuntu, however, I think you have to use "sudo -i" and then "gedit" or "gksudo". However, I've tried to install this, and am not sure of how to launch the program I do not know how to install. There must be a command for launching the file, or installing it. But I am a noob, sorry I can't really help. I am eager for a solution however, because I have a acer with the 950 chipset....

---

### Post by Mark Phelps on 2009-07-08
If you've downloaded the Linux ZIP file and expanded it into a folder, you open a terminal in that folder, enter "sudo GMABooster", and provide your password.  If that doesn't work, try "sudo bash GMABooster". It should then guide you through the rest.

---

### Post by aperture123 on 2009-07-08
> **Mark Phelps said:**
> If you've downloaded the Linux ZIP file and expanded it into a folder, you open a terminal in that folder, enter "sudo GMABooster", and provide your password.  If that doesn't work, try "sudo bash GMABooster". It should then guide you through the rest.

Nope. Doesn't work, I extracted the folder to my desktop directory. Here is what I put into my terminal:
thomas@thomas:~$ sudo GMABooster
sudo: GMABooster: command not found
thomas@thomas:~$ sudo bash GMABooster
bash: GMABooster: No such file or directory
thomas@thomas:~$ sudo -i
root@thomas:~# sudo GMABooster
sudo: GMABooster: command not found
root@thomas:~# sudo bash GMABooster
bash: GMABooster: No such file or directory
root@thomas:~# sudo /thomas/Desktop/haha/GMABooster
sudo: /thomas/Desktop/haha/GMABooster: command not found
root@thomas:~# sudo bash /thomas/Desktop/haha/GMABooster
bash: /thomas/Desktop/haha/GMABooster: No such file or directory

Is there anything else I havent done? YES, I renamed the folder haha, and GMABooster is how its spelled, its their, I tripled check to make sure there are no typos. All I did was download the file, extracted it, read the .txt, rename the folder "haha" in the Desktop directory, and did this in the terminal. Any other ideas? PS I am using Ubuntu 9.04 netbook remix.

EDIT: I did this too:
thomas@thomas:~$ cd Desktop/haha
thomas@thomas:~/Desktop/haha$ dir
data.bin  GMABooster  Readme_GMABooster.txt
thomas@thomas:~/Desktop/haha$ sudo GMABooster
sudo: GMABooster: command not found
thomas@thomas:~/Desktop/haha$ sudo bash GMABooster
GMABooster: GMABooster: cannot execute binary file
thomas@thomas:~/Desktop/haha$ sudo -i
root@thomas:~# GMABooster
-bash: GMABooster: command not found
root@thomas:~# bash GMABooster
bash: GMABooster: No such file or directory
ANY ideas?

---

### Post by moz_21 on 2009-07-14
Assuming you downloaded it to the desktop, open up a terminal, then do the following:

cd Desktop

unzip GMABooster_Linux_09c.zip

(This puts the files directly on the desktop.)

chmod +x GMABooster

(This makes the file executable.)

sudo ./GMABooster

(This runs GMABooster as root from the desktop.)

I tried it, it runs and detects the chip, option "0" detects it runnning at 200MHz. However, trying to set it to different speeds doesn't work for me. Which it shouldn't since mine has i915 graphics. This is under Ubuntu NBR 9.04 with no graphics hacks, on an EEE PC 900.

This also isn't a good way of installing it, but it does allow you to try it out and see if it will work for you.

---

### Post by aperture123 on 2009-07-14
Yes, the above post seems to work, thanks. 
I have verified it is indeed working on the acer aspire 1 as well.:guitar::p

---

### Post by todd99 on 2010-11-21
Preface, I am new to linux and very unfamiliar to terminal.

When I type in the command "cd desktop" it replies with "no such directory or file"

Please help.

> **moz_21 said:**
> Assuming you downloaded it to the desktop, open up a terminal, then do the following:

cd Desktop

unzip GMABooster_Linux_09c.zip

(This puts the files directly on the desktop.)

chmod +x GMABooster

(This makes the file executable.)

sudo ./GMABooster

(This runs GMABooster as root from the desktop.)

I tried it, it runs and detects the chip, option "0" detects it runnning at 200MHz. However, trying to set it to different speeds doesn't work for me. Which it shouldn't since mine has i915 graphics. This is under Ubuntu NBR 9.04 with no graphics hacks, on an EEE PC 900.

This also isn't a good way of installing it, but it does allow you to try it out and see if it will work for you.

---

