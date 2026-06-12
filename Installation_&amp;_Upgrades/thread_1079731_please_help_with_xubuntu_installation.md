---
title: "please help with xubuntu installation"
date: 2009-02-24
forum: Installation &amp; Upgrades
---

### Post by valllllll2000 on 2009-02-24
Hi to all!
I have an ibm thinkpad t20 with windows xp installed on it.
I tried to install xubuntu on it because i read it's good for slow sustems. (it has 250 ram)
When I boot on the xubuntu cd i choose the language and then choose "install xubuntu" and then it seems to load but then I get a black screen. Just that, nothing on it.
What cab I do?
Thks a lot):P

---

### Post by avtolle on 2009-02-24
Take a look at [http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards](http://www.ubuntu.com/getubuntu/releasenotes/810#Hangs%20with%20desktop%20effects%20on%20Intel%20830MG%20and%20845G%20video%20cards) and follow its suggestions to install in safe graphics mode.

---

### Post by valllllll2000 on 2009-02-25
thks avtolle
I did that:
*There is a bug in the Intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and will freeze the system. For new installations, please install using the safe graphics mode (press F4 in the startup screen) on these systems and disable desktop effects via System -> Preferences -> Appearance, clicking on "Visual effects" and choosing "None". *
but then I get like a bleu window with install written on top, which is maybe normal but there is a big I in the middle so I think it's the mouse and I can't move it at all. It's frozen and nothing else happens. So I think there is a problem with the mouse (it's the internal mouse that comes by defect with the laptop and it works ok with windows)

What can I do now?

---

### Post by avtolle on 2009-02-25
I'm far from holding any expertise, but right now, I'd suggest getting the Xubuntu alternate install iso and after checking its md5sum, burn it to a CD-R slowly as an image. The alternate install uses a text-based installer, which often works where the Live CD graphical one doesn't. When installed, you will have a desktop, etc., just as with the Live CD install. You may have similar graphics problems once installed; you may not. 

If you want to try this, when booting the Live CD, select safe graphics mode (via F4 again) and then run "Try xubuntu..."; if you get to the desktop, then disable the effects as set out; and then click on the install folder on the desktop to see if that gets you installed. I'd really suggest using the alternate cd for installation, though; the last time I used a live cd to install any *buntu release was 6.06. I think this shows my age, as I started with personal computers "back in the day" before there were GUIs, and I prefer the text-based installer over the GUI (and, in the case of my Apple ppc machines, the Live CD is a big PIA and have to use the alternate to get installed anyway). Good luck.

---

### Post by valllllll2000 on 2009-02-25
Wow Thks I like this CD much better
I did what you told and the installation started
Then at one point when "select and install software" it didn't work out so I skipped it. Then there was install GRUB and the install LILO I decided to skip them too cause I didn't know what they were and was afraid they might bug too. The next and last step was finish installation so I did that and got the message like:
".....boot manually with the /vmlinuz kernel on partition /dev/sda1 and root =/dev/sda1 passed as kernel argument"
So then I reboot without the CD and it says "no operating system"
So I mean there's nothing there? 
Ok then I tried to boot with CD again and rapair the system but I had to do the things manually so I decided it was too complicated.
NOw I am reinstalling again but shall I install the GRUB and the LILO staff? I don't know what to do. Plus if the software doesn't get installed again will I be able to install it later from the web or something? Does it mean I won't have any programs at all?
Many thanks

---

### Post by avtolle on 2009-02-25
You need to install either GRUB or LILO; bothare boot loaders to get you booted. I've no experience with LILO.

What didn't work out with "select and install software"? Just curious.

---

### Post by valllllll2000 on 2009-02-25
The select and install software says it failed. I tried several times but it just doesn't work. So which one is better to get GRUB or LILO? Or shall I take both? I am new to linux so I don't know.
Thank you

---

### Post by avtolle on 2009-02-25
IMO, GRUB; I don't know anything about LILO, and I've had no problems with GRUB.

EDIT: I'm wondering if your first CD had some problems. The "select and install software", as I understand it, installs a basic system from packages on the CD. Hopefully, this will not happen with the second try.

---

### Post by avtolle on 2009-02-25
One other thought: are you connected to the internet (via a cable) during the installation?

---

### Post by abyrne on 2009-02-25
I, myself, personally like GRUB. Mostly because I've had more experience with it. I've had no experience with LILO. But that's just me

---

### Post by valllllll2000 on 2009-02-25
So it will be GRUB since it got the votes
I am still doing the installation again with the same CD but the thing is the step "select and install software" failed again. It just hangs there for a ling time, doesn't pass 6% and then says "failed" and says I can go to the next step.
Now I am on the next step which is also called select and install software but it's building thin client system. So that works ok. I will try like that and then install the GRUB thing and then give it a try. 
And yes first I started with the Ethernet cable connected, now I took it out cause I need it for the other computer which I am writing on now.
But the step with the software I tried to install it with or without the cable conected and same thing.
Will let you know what happens next.

---

### Post by valllllll2000 on 2009-02-25
Wow it works!! it's wonderful. 
Thank you so much for your help!!!

---

