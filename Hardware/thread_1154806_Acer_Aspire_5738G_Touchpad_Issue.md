---
title: "Acer Aspire 5738G Touchpad Issue"
date: 2009-05-10
forum: Hardware
---

### Post by bmhm on 2009-05-10
Hello every1!

We got a new Acer Aspire 5738G Notebook, 15,6". First step: Remove MS Vista, install Ubuntu 9.04 amd64, of course ;-)

Everything is working fine! Webcam works, external BT is mapped to the Bluetooth key, wireless button and adapter works, correct resolution using nVidias driver. All buttons work, monitor switching works. GREAT! I will soon post it to the laptop testing team (see wiki).
**Edit** Here's the wiki page I just created: [Acer Aspire 5738]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5738")

Well there is just one issue. The "touchpad off" - button is not available on FN+F7, as on models before. Instead it has become a new hardware button, next to the touchpad.  See this picture I've taken:
[[IMG]http://img13.imageshack.us/img13/7138/laptoptouchpad.th.jpg[/IMG]](http://img13.imageshack.us/my.php?image=laptoptouchpad.jpg)

Well the bad thing is, [B][U]I can switch it off - but not on again!
[/U][/B]I watched [FONT="Courier New"]dmesg[/FONT] and [FONT="Courier New"]/var/log/messages[/FONT], but pressing this button is not being logged at all.

Output from [FONT="Courier New"]cat /var/log/Xorg.0.log | grep -i synaptic[/FONT]:
```
$ cat /var/log/Xorg.0.log | grep -i synapt
(II) config/hal: Adding input device SynPS/2 Synaptics TouchPad
(II) LoadModule: "synaptics"
(II) Loading /usr/lib/xorg/modules/input//synaptics_drv.so
(II) Module synaptics: vendor="X.Org Foundation"
(II) Synaptics touchpad driver version 0.99.3
(II) SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5472
(II) SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4448
(II) SynPS/2 Synaptics TouchPad: pressure range 0 - 255
(II) SynPS/2 Synaptics TouchPad: finger width range 0 - 0
(II) SynPS/2 Synaptics TouchPad: buttons: left right middle double triple
(--) SynPS/2 Synaptics TouchPad touchpad found
(**) SynPS/2 Synaptics TouchPad: always reports core events
(II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD)
(**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
(**) SynPS/2 Synaptics TouchPad: (accel) filter chain progression: 2.00
(**) SynPS/2 Synaptics TouchPad: (accel) filter stage 0: 20.00 ms
(**) SynPS/2 Synaptics TouchPad: (accel) set acceleration profile 0
(--) SynPS/2 Synaptics TouchPad touchpad found
```

I didn't file a bug yet. If anyone has an idea, how to proceed, please do so. I'd appreciate it. Thanks in advance.

---

### Post by bmhm on 2009-05-10
Filed at [https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/374459](https://bugs.launchpad.net/ubuntu/+source/xfree86-driver-synaptics/+bug/374459)

I just found out you can re-enable the touchpad by going to Suspend to ram. wired.

---

### Post by haaglin on 2009-06-23
Hi.

I have the same laptop, and same issue. Any news?

---

### Post by bmhm on 2009-06-24
> **haaglin said:**
> I have the same laptop, and same issue. Any news?

It's in X's bugtracker. See the bugtracker on launchpad. In the row "also affects" there is a link to the other bugtracker. This also means: If you like to help, please state it in one of the bugtrackers. It's also been filed at the kernel developer's bugtracker, but I haven't recieved any update since now.

What you can do just right now: log in to launchpad and select "doesn't affect me (change)" so it becomes "affects me too". You may also post a comment on what you've learned about the bug. It will help developers to find out what's wrong.

In general, launchpad is the better place to discuss this bug.

Thanks for replying (now i know I'm not alone ;-) )!

Regards

---

### Post by parsboy on 2009-07-01
Hi All.
I have this problem too. but really this is not annoying me because I use 
pointer Lock (one of Gnome Panel objects ).

Real problem is that HEADPHONE Jack doesn't work. When I insert headphone nothing happens . Do you have Any Idea About This?

 ](*,)

---

### Post by Jonathan_m84 on 2009-08-06
make shure that your button doens't light, then open terminal screen and type this:

sudo modprobe -r psmouse
sudo modprobe psmouse

then your touchpad should work again... it's a workaround, so everytime you press the magic button and want to enable it again, you have to type those two lines ;)

---

### Post by bmhm on 2009-08-07
> **Jonathan_m84 said:**
> make shure that your button doens't light, then open terminal screen and type this

Hi,

that's what I posted on the bug tracker. And you might have it enabled, just press the button afterwards. Weired that it will then switch the touchpad on, isn't it?

Please take a look at the bug reports and try to help. Thanks.

---

### Post by bmhm on 2009-09-05
Yay, it has been fixed:

> Comment #1 From  Dmitry Torokhov   2009-09-05 05:29:09   -------

Should be fixed by the following commit:
ced909ff048c9950e211783417f3c01361f3be28

On older kernels the problem can be worked around with i8042.nomux option.
*Source:* [http://bugzilla.kernel.org/show_bug.cgi?id=13363](http://bugzilla.kernel.org/show_bug.cgi?id=13363)

Can someone explain how to 
[LIST]
[*] view change ce...
[*] apply this option? Is the option for the module or kernel...?
[/LIST]

Thanks in advance.

---

### Post by peachtree195 on 2009-10-13
I am relatively a newbie here, has the issue been resolved finally? It is hard for me to understand what is going on exactly right now.

I am working on acer 5738 the mouse accidentally redirecting my cursor is extremely annoying. After turning touchpad off I can go back to using mouse by using command line in terminal but what i am looking for is a permanent solution to this problem - click off, click back on. I have browsed a lot for it, browsed around the launchpad but i could not figure out what it all means that much, what is the status or how to fix it permanently. 

The same with [http://bugzilla.kernel.org/show_bug.cgi?id=13363](http://bugzilla.kernel.org/show_bug.cgi?id=13363) where it is supposedly fixed but i do not know how to update the patch myself - does it just come within the applications update of ubuntu or you would have to install it somehow? 

And lastly - does it work for you already or not yet?

Thank you!

---

### Post by bmhm on 2009-10-15
> **peachtree195 said:**
> The same with [http://bugzilla.kernel.org/show_bug.cgi?id=13363](http://bugzilla.kernel.org/show_bug.cgi?id=13363) where it is supposedly fixed but i do not know how to update the patch myself - does it just come within the applications update of ubuntu or you would have to install it somehow? 

As I answered via pm already, this is a kernel issue. You will have to wait for Ubuntu Karmic (8.10). There will never be a new kernel on an existing Ubuntu.
Compiling a kernel on your own is a possibility, but I highly discourage you from doing so. It's a quite sophisticated procedure, and you can do a lot of wrong things which will cause Ubuntu not to work correctly or start anymore.

As soon as karmic is being released, your update manager tells you about it. Then you can just klick "upgrade to karmic" and you will receive the mentioned update.

---

### Post by sammy888 on 2009-10-29
OK, new Ubuntu (9.10) has been relesed, but problem still remains. Any new idea how to fix this problem?

---

### Post by thered on 2009-10-31
I'm here because I'm thiking of purchasing a 5738 just checking the compatibility with Ubuntu.

Am I right in thinking the touchpad works ok but wont restart after being switched off without running some terminal commands?

---

### Post by sammy888 on 2009-11-08
That's right. And also Bluetooth button adjust brightness and control BT ON/OFF. [Here]("https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire5738") is more info.

---

### Post by bmhm on 2009-11-09
Good news! HDMI sound output works in 9.10, even out of the box!

---

### Post by bmhm on 2009-11-09
> **sammy888 said:**
> OK, new Ubuntu (9.10) has been relesed, but problem still remains. Any new idea how to fix this problem?

Probably I got one.

Can you try this please (works on grub1)
[LIST]
[*]Just before booting into ubuntu, press Escape. Grub (the boot loader) should open.
[*]Now press "e" to edit the first bootline, 
[*]then press arrow down to reach the line which says "quiet" and "splash" (or one of those).
[*]Press e again.
[*]Append this to the line: **i8042.nomux**
[*]Press enter to leave edit mode.
[*]Press '**b**' to boot into ubuntu.
[/LIST]

Now, does it work? Cannot test it myself right now...

---

### Post by OrnithO on 2009-11-13
> **bmhm said:**
> Probably I got one.

Can you try this please (works on grub1)
[LIST]
[*]Just before booting into ubuntu, press Escape. Grub (the boot loader) should open.
[*]Now press "e" to edit the first bootline,
[*]then press arrow down to reach the line which says "quiet" and "splash" (or one of those).
[*]Press e again.
[*]Append this to the line: **i8042.nomux**
[*]Press enter to leave edit mode.
[*]Press '**b**' to boot into ubuntu.
[/LIST]

Now, does it work? Cannot test it myself right now...
 Worked for me on three different laptops: Acer Timeline 4810T and 4810TZ and Acer Aspire 5738Z-424G25Mn with Ubuntu 9.10 64 bits and the new grub.

---

### Post by sammy888 on 2009-11-29
At the moment, I don't have Linux on 5738G, but I am curious if the problem with BT button has been fixed?

P.S. So touchpad problem has been fixed? :D

---

### Post by thered on 2009-11-30
I've just tried the above i8042.nomux procedure on my 5738z.  Had to remove it, touchpad scrolling totally erratic.

I can't get gsynaptic (Touchpad) to run -get the following alert: 

"Gsynaptics couldn't initialize.
You have to set 'SHMConfig' 'true' in xorg.conf or XF86Config to use GSynaptics"

Touchpad is very poor to use, sometimes won't respond to 'tapping'.

If the 'disable touchpad' button is pressed it will not start, as per first posting.

So no, I still think there are a few issues with it.

Can anyopne help on above alert?

edit: I've just tried this:

xxxx@laptop3:~$ synclient -l

Couldn't find synaptics properties. No synaptics driver loaded?

Sol ooks like not recognising it at all

---

### Post by sammy888 on 2010-03-03
Hi! 
I am writing after a long time ;). So I must ask if there is any progress with "Bluetooth button problem"?

---

### Post by openware on 2010-05-08
There is no problem with the BT button it is working but just visualy is not correct. The problem with the touch pad button still remaining now has visual representation too but not turns on the pad.

---

### Post by bmhm on 2010-05-08
Hi,

I reopened the bug at kernel.org.

Please post your experiences there if you have new information.

[http://ubuntuforums.org/showthread.php?t=1154806&page=2](http://ubuntuforums.org/showthread.php?t=1154806&page=2)
[https://bugzilla.kernel.org/show_bug.cgi?id=13363](https://bugzilla.kernel.org/show_bug.cgi?id=13363)

Thanks & Regards,
Ben

---

### Post by Criminal.Sausage on 2010-07-21
Sorry for digging up a (dead?) old cow, but I might have found a simple workaround. I posted this to launchpad too. As I'm in somewhat of a hurry, I will simply copy paste.



I'm on a HP Pavillion, but I've experienced the same problems. I was reluctant to try the nomux fix, as it requires some work in getting the touchpad working properly again. Anyway, in my case bash and the keyboard stopped working, except for a few buttons. All the F-keys and the bottom row still worked. The only chance it gave me was some ctrl-alt-F# combinations. And miraculously one combination worked for me:

First press ctrl-alt-F1 (takes you to a login screen)
Then press ctrl-alt-F7 and everything should be fine again.

---

### Post by fbobraga on 2010-08-29
adding the ***i8042.nomux*** fixed the touchpad issue here (in my Acer Aspire 5738 - I've setup it in */etc/default/grub*), but the **brightness** control still doesn't work...

---

### Post by fbobraga on 2010-08-29
brightness issue fixed here by [http://ubuntuforums.org/showpost.php?p=8411337&postcount=5](http://ubuntuforums.org/showpost.php?p=8411337&postcount=5) (info on various issues: [https://help.ubuntu.com/community/AspireTimeline/Fixes]("https://help.ubuntu.com/community/AspireTimeline/Fixes"))

---

### Post by tb2012 on 2011-12-13
.
Acer Aspire 5738dg added "**i8042.nomux**"(without "") **to** grub.cfg ... it works ... happy camper :D
.
System: Ubuntu 10.10 Kernel 2.6.35-31-generic-pae
.
.
in detail for newbies like me (UUID 0xxxxxxxxxxxxx is sample),** BOLD** just for highlighting:
.
> cd /boot/grub
sudo cp grub.cfg grub.cfg.bak
sudo gedit grub.cfg
find & paste **i8042.nomux** into line
.
linux /boot/vmlinuz-2.6.35-31-generic-pae root=UUID=0xxxxxxxxxxxxxxx loop=/ubuntu/disks/root.disk ro   quiet splash nomodeset  video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
.
so it looks like this
.
linux /boot/vmlinuz-2.6.35-31-generic-pae root=UUID=0xxxxxxxxxxxxxxx loop=/ubuntu/disks/root.disk ro   quiet splash nomodeset **i8042.nomux **video=uvesafb:mode_option=1280x1024-24,mtrr=3,scroll=ywrap
.
reboot or sudo grub update.
.
.
.
[COLOR=Red]***Now I just need this annoyance fixed ***[/COLOR];)
.
*On my Acer Aspire 5738dg (with bluetooth adapter) when the bluetooth button is pressed the laptop screen brightness notification is  displayed.  The blue tooth icon fades to off as it should. *
....

---

