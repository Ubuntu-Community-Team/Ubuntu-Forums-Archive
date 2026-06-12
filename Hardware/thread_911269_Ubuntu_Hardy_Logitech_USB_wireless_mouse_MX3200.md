---
title: "Ubuntu Hardy Logitech USB wireless mouse MX3200"
date: 2008-09-05
forum: Hardware
---

### Post by pokeyoats on 2008-09-05
Good day all,

Sigh, I'm beginning to remember why I gave up on Linux so many years ago. I am however giving it another go because I was unfortunate enough to have a cheating girlfriend that got her "IT F*** buddies" to completely decimate my Vista machine.

In the end they setup a Domain controller, got my machine on it and overided all my security policies so that not even a local administrator could change it back. At least Linux is more secure in that regard, but irrespective, I now have a bad taste in my mouth regarding Vista.

Here however is my problem (besides the cheating girlfriend, whom I got rid off :)).

I have a Logitech MX3200 wireless USB mouse that worked flawlessly during the install from the Ubuntu 8.04 Hardy Live CD. In fact, I have deliberately left the live CD running for over a day to prove that the MX3200 works, continues to work, and never freezes.

This however is not the case when I boot into my "Installed" version of Ubuntu. After a few minutes of activity, the mouse will freeze and stop responding completely. Unplugging the USB device and plugging it back in achieves nothing. Ironically, if I plug a PS/2 mouse along with the USB one and reboot, then after the USB mosue freezes, the PS/2 mouse continues to work. And no, booting without the PS/2 mouse plugged in does not alleviate the problem.

This is why I will never understand all of the "Linux is the best, I'm never using Windows again" banter that flows so freely around. The reality is that Linux is "always in development" and for most people, just never quite works right. That said, I'd love to be proven wrong.

A factor I believe contributed to the freezing problem was the installation of the ATI accelerated video drivers (which thanks to desktop cube (now cylinder (compiz-fusion 0.7.6)) I do NOT want to give this awesome 3D desktop up for a mouse, and nor should I!!

I would greatly apprecaite some help as I am about to go and waste $20 on a PS/2 mouse with scroll wheel so that I can use Hardy more effectively. But this is far from an elegant solution and given that the Live CD supports my MX3200 mouse and keyboard combo perfectly, I don't understand why this purchase should be necessary.

Any help that could be given would be immeasurably valued!!

---

### Post by at0mic on 2008-09-08
im going to buy the mx3200 as im pretty sure i can get it work one way or another. i'll let you know how it goes in a few days. 

from what i gather you should setup encrypted wireless on a windows box for the keyboard and then to get the misc buttons on the mouse to work use this guide: [http://blog.verkoyen.eu/2007/10/08/howto-ubuntu-logitech-mx3200-cordless-laser-set/](http://blog.verkoyen.eu/2007/10/08/howto-ubuntu-logitech-mx3200-cordless-laser-set/)

there was mention of a 3rd party making drivers for the logitech mice which coudl help you. [http://www.hidpoint.com/home.html](http://www.hidpoint.com/home.html) . i think the mx3200 set has a mx600 mouse

[http://www.hidpoint.com/forum/func,view/catid,15&id=/id,24/catid,15/](http://www.hidpoint.com/forum/func,view/catid,15&id=/id,24/catid,15/)

---

### Post by pokeyoats on 2008-09-10
Good day Atomic,

Thank you ever so much for your reply, it is greatly appreciated.

I can assure that the mouse/keyboard combo is setup correctly, along with the Wireless encryption aspect. I further verified that the encryption was setup correctly because I can use the keyboard/mouse on my XBOX 360 just by plugging the USB receiver in.

Previously, i.e. before setting up the encryption, the keyboard would not work on the 360.

I will however investigate the other links that you have kindly posted and hopefully can report back some success.

The only other thing I can think of is trying to figure out what it is that allows the mouse and keyboard to work perfectly when using the Hardy 8.4 Live CD. I can leave that running for days and the mouse/keyboard continue to work.

Thank you kindly,
Pokey Oats.

P.s. Despite my reservations regarding crappy driver support and sheer length of time for hardware support regarding Linux, I do have to concede that after one day of running Firestarter and Etherape that Linux is now my preferred OS, if for no other reason but because of how damn safe I feel.

Admittedly, it's not Vista's fault I had a cheating girlfriend that gave "someone" access to my machine; but I was quite unimpressed by the fact that an external (DC based) security policy can lock out a Local Administrator...

---

### Post by at0mic on 2008-09-11
granted linux takes longer to setup. but once it is setup it is so sweet and way more efficient than windows. I use linux all the time for work and just started using it as a multimedia / general browser box [aka primary computer] THe power is in what you can get linux to do for you as opposed to you doing every step like with windows. Newsgroup downloading for example, i can drop a nzb into a folder and have it automatically download, check for errors and fix if needed, then extract... thats efficiency!. last piece of my puzzle is a wireless mouse and keyboard. I also have to figure out how to get linux to automatically download stuff to my 4TB system using keywords but im sure that can be accomplished to.

---

### Post by at0mic on 2008-09-12
12:30 update:got my wireless gear today and happy to report 0 issues with the mouse aside from the zoom buttons not working. worked as soon as i plugged the secure connect usb device into the rear usb ports and hit the button on it. also interesting to know i have both the connected usb mouse and wireless mouse working at the same time. the forward/back buttons for browsing do work on the mouse for firefox which is useful.

12:50 update: NOte that i origionally installed ubuntu with a usb mouse. also note i dont have the keyboard connected at all yet.

1:08pm update: connected the wireless keyboard using only linux and the connect button on the keyboard. no serious issues. a lot of the extra buttons work and alot of the others do not. bit of lag as im typing . but im a really fast typer and is not essential to have 0 lag for multimedia. no encryption is setup yet. i have to wait for my raid 5 to repair itself on my windows box before i set the encryption. also interesting to know i have both the wireless and usb keyboard connected and functioning at the same time. update later.

---

### Post by IntuitiveNipple on 2008-09-12
> **pokeyoats said:**
> Good day all,

This however is not the case when I boot into my "Installed" version of Ubuntu. After a few minutes of activity, the mouse will freeze and stop responding completely. Unplugging the USB device and plugging it back in achieves nothing.
Can you attach a (compressed) copy of /var/log/kern.log that covers the period when the mouse freezes, and the attempts to fix with the unplug/plug sequence?

---

### Post by prashime on 2008-09-25
See this.....

[http://www.hidpoint.com/latest/support_for_2.6.24-19_and_smp_kernels.html](http://www.hidpoint.com/latest/support_for_2.6.24-19_and_smp_kernels.html)

---

### Post by madestro on 2008-10-16
> **prashime said:**
> See this.....

[http://www.hidpoint.com/latest/support_for_2.6.24-19_and_smp_kernels.html](http://www.hidpoint.com/latest/support_for_2.6.24-19_and_smp_kernels.html)
I think this did it for me since I downloaded the hidpoint bin file and started the installation in 7.10 BUT I couldn't finish it since I couldn't move the mouse to the check box on the license agreement. So I restarted my box and when I tried to reinstall it gave me an error of another setup already running (I don't know how to view those open aplications and kill them, sorry) and even though I've not tried to install again the hidpoint my mouse problems went away, I even managed to update to 8.04 LTS and use the restricted drivers for my geforce 7950 and zero issues so far.
So thanks a lot to **prashime** and all the other posters on this forums for the help.
As a commercial I would suggest trying out the Quickstarter app from *[http://quickstart.phpbb.net/viewtopic.php?f=8&t=11](http://quickstart.phpbb.net/viewtopic.php?f=8&t=11)* it's an awesome app to backup the system and much more.

---

### Post by mauropat on 2009-01-01
Happy new year to everybody !

This is my second year with Ubuntu: everything was really fine with Ubuntu my desk and my laptop but few days ago I tripped over a problem with my Hardy Heron on the desktop. Before that point everything was perfect but now I do not have anymore the control of the mouse and sometime of the keyboard 

(Logitech Cordless Desktop MX3000). 

For example I can right-click on the desk and on the icons but the left-click doesn't work! on the menu panel on the top of the desk the left click works ! with some application windows the right and the left clicks work fine, with some windows just one works, with other no click works. with some windows theh keyboard works neither. I tried to change the keyboard preferences on the System menu -> Preferences -> keyboard but without having good results.

The best is when I invoke the Update Manager GUI and I press the "Install Updates" bottom: a box appears with the text: "***Could not grab your mouse**. A malicious client may be eavesdropping on your session or you may have just clicked a menu or some application just decided to get focus. Try again.*"
At this point the only interaction with the Hardy the  mouse pointer motion on the desk: no action is permitted (as L/R-click, Ctrl+Alt+L, other), just Ctrl+Alt+BackSpace let me logout.

Thanks for all the suggestions

---

### Post by mauropat on 2009-01-01
I was forgetting: I tried the 8.10 live, but the problem is still there.

thanks again

---

