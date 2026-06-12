---
title: "Can't boot (black screen), except using recovery + resume (Pavillion DM4)"
date: 2012-02-20
forum: Hardware
---

### Post by mfpompadour on 2012-02-20
I have a Pavillion DM4.

I recently upgraded to Oneiric. This is when the problem began.

When I boot, if I select the normal kernal (3.0.0.16), I get the Ubuntu image with the loading dots, but then I get a black screen, not the login screen. I cannot CTRL-ALT-F1 to the prompt.

However, I can boot correctly by booting that kernel in recovery mode, giving the boot messages, and then selecting the "Resume" recovery option, which correctly loads the login manager.

Another issue is that when my laptop hibernates/suspends (I'm not sure which), and I reactivate it, I am stuck with a black screen.

How do I resolve this?

---

### Post by rtalcott on 2012-02-21
I have a dm4 and I had a problem that was almost the same...fine install on 11.10 and 12.04 then a black screen on boot...I had to add nomodeset to the boot options to give me a screen...this did it for me:

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

now I need to figure out how to get the correct screen resolution...my dm4 only has the Intel integrated graphics.
rt

---

### Post by roelforg on 2012-02-21
I had a color/screen issue too; nomodeset locks your resolution to VESA.

Let me see what i did to fix it...
Oh; i remember:
sudo to root andmodify /etc/default/grub
There should be a line starting with: #GRUB_GFXMODE replace it with this:
```

GRUB_GFXMODE=text

```
and issue a sudo update-grub
Your bootscreen won't look to pretty (it's like viewing with low res) but it'll work.
(note: remove nomodeset and if you don't mind the looks, remove quiet and splash as well; you'll see the kernel messages scroll by, though i find that it looks kinda cool and hackerish)

(I'm giving you this info from my exp with graphics problems)

---

### Post by roelforg on 2012-02-21
Though i'm assuming your pc will still boot;
if it doesn't, i'd like to know if your caps-lock kb-light will start blinking; it'll mean there's kernel issue removing the quiet and splash bootopts should let the kernel display it's deathscreams and tell you what's wrong; like always: google is your friend)

---

### Post by rtalcott on 2012-02-21
roelforg...Thank you!  You explained why I am trapped in the wrong resolution (VESA)...I'll try your fix later on today when I have more time...again...Thank you!
rt

---

### Post by roelforg on 2012-02-21
> **rtalcott said:**
> roelforg...Thank you!  You explained why I am trapped in the wrong resolution (VESA)...I'll try your fix later on today when I have more time...again...Thank you!
rt
Sure man,
We're all here to ask and answer questions.

Feel free to ask when there are more problems.
And i let me tell you:
My pc has a 21.5" screen hooked up to it, max resolution 1920*1080;
when nomodeset is on, resolution drops to 1024*768 and won't get higher until i disable nomodeset.

---

### Post by mfpompadour on 2012-02-22
> **roelforg said:**
> 
sudo to root andmodify /etc/default/grub
There should be a line starting with: #GRUB_GFXMODE replace it with this:
```

GRUB_GFXMODE=text

```and issue a sudo update-grub
Your bootscreen won't look to pretty (it's like viewing with low res) but it'll work.
(note: remove nomodeset and if you don't mind the looks, remove quiet and splash as well; you'll see the kernel messages scroll by, though i find that it looks kinda cool and hackerish)


So I should follow JUST your instructions and NOT do nomodeset?
Just want to be clear.

---

### Post by rtalcott on 2012-02-22
IMO nomodeset isn't a great solution but at least I got away from the black screen but I cannot get away from 1024x768 and that's still a problem...I'm also running 12.04 Alpha and the hardware in general is not happy yet.

However...at this point I have not tried anything else.
rt

---

### Post by roelforg on 2012-02-22
> **rtalcott said:**
> IMO nomodeset isn't a great solution but at least I got away from the black screen but I cannot get away from 1024x768 and that's still a problem...I'm also running 12.04 Alpha and the hardware in general is not happy yet.

However...at this point I have not tried anything else.
rt
I don't wanna troll here.
But there's a special forum for 12.04 where they know more about 12.04 than i do.
They'll probably be able to help you much better.

EDIT: Wait, did you mean multiboot 11.10 - 12.04? The 11.10 i can help you with, the 12.04 not.

---

### Post by mfpompadour on 2012-04-30
> **roelforg said:**
> I had a color/screen issue too; nomodeset locks your resolution to VESA.

Let me see what i did to fix it...
Oh; i remember:
sudo to root andmodify /etc/default/grub
There should be a line starting with: #GRUB_GFXMODE replace it with this:
```

GRUB_GFXMODE=text

```and issue a sudo update-grub

Hmmm.... I tried this and I still get a black screen and can't do anything.
This is after the initial Ubuntu loading image.
How can I figure out what is going on?

---

### Post by EngineersGarage on 2012-04-30
there is a easy fix to get blank screen up... in terminal just run " setpci -s 00:02.0 F4.B=00 " 
then as root, "sudo nano /etc/rc.local

enter the same code just before " exit 0 " press F3 to write,enter to confirm, then Ctrl-x to exit. 
Reboot and screen is fixed. 

Im still searching for fix for sleep and hibernation... I know it is on the net because i did it before with help but cant remember where I got the info from/...

---

### Post by mfpompadour on 2012-05-04
> **EngineersGarage said:**
> there is a easy fix to get blank screen up... in terminal just run " setpci -s 00:02.0 F4.B=00 " 
then as root, "sudo nano /etc/rc.local

enter the same code just before " exit 0 " press F3 to write,enter to confirm, then Ctrl-x to exit. 
Reboot and screen is fixed. 

Im still searching for fix for sleep and hibernation... I know it is on the net because i did it before with help but cant remember where I got the info from/...

I don't understand. I should boot using Recover mode, log into X, and then type these instructions into a terminal? What do they do?

---

### Post by matt082606 on 2012-05-05
I'm assuming you have my same issue:

[http://ubuntuforums.org/showthread.php?t=1889258]("http://ubuntuforums.org/showthread.php?t=1889258")

If so know that the fix I outline in that post only works on first boot-up, not waking up from sleep.

What I do for that is first type my password in the dark and hit enter to login, then use ctrl+alt+t to open a terminal, type sudo su then my password again and enter. then I press up key twice and enter.

This only works of course if your last two sudo commands were:
```
setpci -s 00:02.0 F4.B=00
```

and then:
```
exit
```

I have been making sure to run those two when exiting sudo when I use the terminal.

I am currently searching for a more permanent solution to the waking from sleep but nothing I have tried yet seems to work. I will post a follow up if/when I get it fixed completely.

---

### Post by mfpompadour on 2012-05-06
> **matt082606 said:**
> I'm assuming you have my same issue:

[http://ubuntuforums.org/showthread.php?t=1889258](http://ubuntuforums.org/showthread.php?t=1889258)

If so know that the fix I outline in that post only works on first boot-up, not waking up from sleep.

What I do for that is first type my password in the dark and hit enter to login, then use ctrl+alt+t to open a terminal, type sudo su then my password again and enter. then I press up key twice and enter.

This only works of course if your last two sudo commands were:
```
setpci -s 00:02.0 F4.B=00
```and then:
```
exit
```I have been making sure to run those two when exiting sudo when I use the terminal.

Do you need to do this only once and then it works from then on? Or do you have to do this repeatedly?

---

