---
title: "Old video card dead - put a used old card in but no display"
date: 2014-01-25
forum: Hardware
---

### Post by Broad_ripple on 2014-01-25
I have an old HP N377M Media Center with 2 gig memory. I know it's old but it runs Ubuntu (12.10) great. The old video card started going out. I know it was the card because I tried 2 different other monitors which displayed the same problem (screen would flicker and then go blank). I found that if I turned the monitor on and off repeatedly I could get a display (but what a hassle and after a while even this won't work). The old card is an AGP type card. I found that I had an old box that had an AGP in it which was working okay last used. So I put the functioning card in and booted up, but I don't have any display, not even a cursor.The bad card had 128M but the replacement only has 32 (this may be part of the problem).

I have a windows machine which I am using right now to get on the forum, but sure would like to get that old box working because there is a lot of data on the drive there and I really like using Ubuntu.

I am looking to buy a much better AGP card on ebay (512M) but even if I get a new card I'm pretty sure I will still get a blank screen just as I do right now (missing drives, etc.).

I did some searches here about new graphic cards/blank display but there were a lot of hits about 'x start' and such which I know nothing about. But even if I did, not sure what one can do if you have a blank screen.
 
Any help would be appreciated.

Bill

---

### Post by jp734 on 2014-01-25
What was the old (dead) card and what's the old functioning 32mb card. Are they the same brand? And even if they are the same, doesn't mean driver will work for both. So I would suggest if you have any configuration file that you move it somewhere in case you need it for later use and then reboot your pc and just let it use default settings

---

### Post by Broad_ripple on 2014-01-25
The old card is a HP 5187/4862 [h=2]HP Graphics Card Ati Radeon 9200 Ntsc Mfr P/N 5187-4862[/h]
The substitute card is an ASUS V3800M.

I do think I could move the config but not sure how to go about it without a display.


After the box has booted, I'm sure it is sitting at the password request. I could then enter the password which would get me in blind. Is there a way to open the terminal by a certain combination of key stokes? Then perhaps I could move the config and reboot with default settings?

Thanks for your suggestion.

---

### Post by deadflowr on 2014-01-25
ctrl + alt + F1 (or F2-6)
should get you into a console/terminal login.

---

### Post by Broad_ripple on 2014-01-25
Okay, that should give me some access.

What terminal command would reset me to default settings?

Thanks so much.

---

### Post by deadflowr on 2014-01-25
Do you remember installing drivers for the ole dead card?
Quite possibly it would've been the fglrx drivers(those are the ati closed source drivers, the open source drivers for the card are already included in Ubuntu, no charge:P)
In which case you would remove the fglrx and the control center fglrx-amdcccle
Example would be
```
sudo apt-get remove fglrx fglrx-amdcccle
```
But that would rely on those drivers being the drivers installed.

In addition, you would also probably need to remove the xorg.conf file
```
sudo rm /etc/X11/xorg.conf
```

On top of this all, a blank screen might mean you'll need to set the nomodeset parameter in grub
grub is easier to edit from the grub boot screen(simply press 'e' to edit and add the word nomodeset to the line that has GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" so it'll look like this 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"
If getting grub boot menu isn't easy, then edit it in the file /etc/default/grub
In the console try
```
sudo nano /etc/default/grub
```
find the line there and do the above then save and exit.
I find the easiest is to press ctrl + x which will save and exit nano.
then run 
```
sudo update-grub
```
to make the changes take effect.

Even still, I'm not so sure any of this will work, but it's something to start with.

Added: Somehow I seriously doubt that you had the fglrx drivers installed.
Maybe the fglrx-legacy drivers, but not the normal ones.
Cards too old.

---

### Post by Broad_ripple on 2014-01-25
Wow, okay, makes sense, but quite an endeavor without a display. I'm going to give it a go. 

Thanks for your help on this. You know your stuff.

---

### Post by deadflowr on 2014-01-25
> **Broad_ripple said:**
>  You know your stuff.

Not really.
these are all just the most common solutions to that type of problem.
But it doesn't mean it's the right solutions for your problem.
Like I stated before, I'm not sure if it'll actually work or not.

But good luck, anyway.

---

### Post by Yellow Pasque on 2014-01-26
Just a note for anyone reading,
ASUS V3800M = TNT2 chipset

---

