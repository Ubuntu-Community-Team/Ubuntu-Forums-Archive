---
title: "Help- Cant install unbuntu 9.04."
date: 2009-05-24
forum: Installation &amp; Upgrades
---

### Post by Sikez on 2009-05-24
Help- Cant install unbuntu 9.04.
I have several machines.
I have tried to install unbuntu 9.04 on everyone, thinking maybe it was A hardware issue.
All different types of video cards etc./amds/P4's P2s,Celeron.
I tried installing with all different types of settings etc on each machine.
Safe Graphics mode etc.
Tried downing the  software time and time again, maybe thinking it was corrupt and re burning it on different machines and differnt CD's.
I have tried with and without a KVM switch etc, different monitors,mouses,keyboards also.

Here is the issue.
It get's to the main screen after choosing Install , the orange bar runs and it just goes to a black screen.
[COLOR=Red]**On one computer , it went blank then an orange screen appeared. with the curers frozen.**[/COLOR]
I have spent countless hours, trying to get this to work with no luck.
I have searched these forums and tried all different kinds of stuff and suggestions-nothing works.
What am I doing wrong?
**Any help would be appreciated.**

---

### Post by Sef on 2009-05-24
Instead of installing or running the live cd, go down to 'check disk for errors' (or something similar.)  Make sure the disk is good first.

---

### Post by presence1960 on 2009-05-24
some basic stuff to check: did you burn it to a CD-R and NOT a CD-RW? Did you checksum? Did you use the Check Disk for Defects option instead of choosing Install when you booted it? When you burned it did you burn it at a slower speed? Maybe try burning another disk. Or try using the text based alternate installer. It can be downloaded here : [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors)

---

### Post by Sikez on 2009-05-24
> **Sef said:**
> Instead of installing or running the live cd, go down to 'check disk for errors' (or something similar.)  Make sure the disk is good first.

Results:  Error found in 1 file.

---

### Post by Kareeser on 2009-05-24
That answers your question. You need to redownload it, check it against its md5 has with the command "md5sum", and burn it to a CD-R at the slowest speed possible.

---

### Post by presence1960 on 2009-05-24
> **Sikez said:**
> Results:  Error found in 1 file.

bad burn. hopefully it isnt your .iso that is bad. if your .iso is bad you will need to download it again. I would try burning another CD-R and see what happens, if the same thing happens then your .iso may be corrupted.

---

### Post by Sikez on 2009-05-24
> **Kareeser said:**
> That answers your question. You need to redownload it, check it against its md5 has with the command "md5sum", and burn it to a CD-R at the slowest speed possible.

Ok- Thank you.

---

### Post by Sikez on 2009-05-24
Got a good LiveCD burnt, scanned with no errors.

However both times i tried to install ....It gets to the Welcome setup screen.
I choose English and hit Forward and it just freezes. with the icon going in circles.
What would cause that?
Comp ran fine & fast with winXP on it, so i know it is good.

---

### Post by presence1960 on 2009-05-24
try the text based alternate installer. Go to the link in post #3 of this thread.

---

### Post by Sikez on 2009-05-24
> **presence1960 said:**
> try the text based alternate installer. Go to the link in post #3 of this thread.

Got it installed ,using the method you suggested.


LOL NOW... when it starts up I get this message.

" Ubuntu is running in low graphics mode.

The following errors were encountered.

You made need to update your configuration to solve this.

Intel Failed to pin front buffer. Cannot allocate memory. "

Then I hit **OK** and the screen just goes black and does nothing.
Reboot - Same thing.

---

### Post by Sikez on 2009-05-24
Any ideas...anyone?

Tried to google the error and all I got was a page from bugtraq stating the same error.

" Ubuntu is running in low graphics mode.

The following errors were encountered.

You made need to update your configuration to solve this.

Intel Failed to pin front buffer. Cannot allocate memory. "

---

### Post by oldos2er on 2009-05-24
Is that an Intel video card?

 Try booting into recovery mode and run 'xfix'.

---

### Post by Sikez on 2009-05-24
> **oldos2er said:**
> Is that an Intel video card?

 Try booting into recovery mode and run 'xfix'.


That was the first thing I tried.
Yes , Intel vid card.

It didn't resolve the error.

---

### Post by Sikez on 2009-05-24
Just finished installing on PC#2 .

Got the same error except when I hit **OK **it took me to another window and I checked the sever log.
"**Cannot locate core pointer device.**"


Then when I exit out of it and try login to console the screen just goes black.

Edit: Rebooted and got to the login console.

Tried to startx - and just got a Fatal Server Error:
[COLOR=Red]**Couldn't bind memory for B0 front buffer.**[/COLOR]

---

