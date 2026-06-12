---
title: "ATI problem 5770 HD My screen says out of range"
date: 2009-11-10
forum: Hardware
---

### Post by death soldier on 2009-11-10
After upgrading to ATi 5770 HD RAndeon on Ubuntu 9.10 and installing the fglrx close source  drivers.When booting and the splash screen is supposed to show my screen blacks out and  says OUt of range ....

---

### Post by patmir on 2009-11-10
mmm yes... I've seen this problem before. Yesterday. At your house

---

### Post by PiV on 2009-11-26
I feel really sad #-oto hear this as I am orders this graphic card to go with my new i7 

I hope there will soon be a problem because I would like to try out this new ubuntu on my new machine

Good luck and if anyone knowns anything about this issue please reply :D

---

### Post by lisati on 2009-11-26
Was this an update via update manager or a clean install?

If an update, and you didn't update grub to grub2, there's a setting in menu.lst somewhere that might be of help... give me a moment, I think there's a thread somewhere which touches on this.


Edit: this might help if you're still using grub and not grub2: [http://ubuntuforums.org/showpost.php?p=4348704&postcount=14](http://ubuntuforums.org/showpost.php?p=4348704&postcount=14)

Edit 2: Another option, that I've used myself with grub (NOT grub2) is to change the line in /boot/grub/menu.lst that reads: ```
# defoptions=quiet splash[/quote] to read [quote]# defoptions=quiet nosplash
``` - if you choose this option, you'll need to save the file and then enter ```
sudo update-grub
```. **Important:** this suggestion is for grub, not the grub2 that is default for a clean install of 9.10

---

### Post by death soldier on 2009-12-01
it was a clean install..
However from what I can tell I have grub 1.94 beta installed.
how can I update to grub 2?
and is it really necessary?

---

### Post by Ganaveh on 2009-12-03
You must change the display setting in control panel of the video-card driver program(like ATI catalyst control center)

---

### Post by Yellow Pasque on 2009-12-03
Did you install Catalyst 9-11? (the version that comes with Ubuntu is based off Cat. 9-10)

Cat. 9-11 is the first AMD driver to properly support your card: [http://www.phoronix.com/scan.php?page=news_item&px=NzcxNA](http://www.phoronix.com/scan.php?page=news_item&px=NzcxNA)

---

### Post by death soldier on 2009-12-08
i Try that driver but it say problem and can continue

---

