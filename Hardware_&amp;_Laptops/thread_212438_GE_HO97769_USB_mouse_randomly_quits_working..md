---
title: "GE HO97769 USB mouse randomly quits working."
date: 2006-07-09
forum: Hardware &amp; Laptops
---

### Post by hygraed on 2006-07-09
I have a General Electric HO97769 optical USB mouse. Recently, it has randomly quit working when I am using Ubuntu, and I have to revert to my laptop mouse. I can use the computer for up to fifteen minutes after a restart, and then it just stops responding.
Any suggestions? Has anyone else had this problem?

---

### Post by hygraed on 2006-07-11
bump

Please help, if you need more info just ask

---

### Post by terrapin on 2006-07-13
I'm having the same problem. I have a Logitech cordless usb mouse and it works fine for 10 or 15 minutes after I boot up and then quits working completely.

This same mouse has been working perfectly up until today.

Thought it might have something to do with /etc/X11/xorg.conf because I recently installed a proprietary driver from ATI, so I reverted to my backed-up version of xorg.conf, rebooted, mouse worked for 10 min then stopped :-k

---

### Post by terrapin on 2006-07-13
If you are using fglrx drivers, check this out:
[http://www.ubuntuforums.org/showthread.php?p=1250888#post1250888]("http://www.ubuntuforums.org/showthread.php?p=1250888#post1250888")

---

### Post by hygraed on 2006-07-19
How would I switch from fglrx to ati drivers? What would I change in xorg.conf?

---

### Post by terrapin on 2006-07-20
You should be able to open /etc/X11/xorg.conf and replace "fglrx" with "ati":
sudo gedit /etc/X11/xorg.conf
Then restart.

Another option is to look in the /etc/X11/ directory for an older, backed-up version of your xorg.conf that isn't setup to use fglrx. Replace current xorg.conf with back up.

---

### Post by hygraed on 2006-07-21
> **terrapin said:**
> You should be able to open /etc/X11/xorg.conf and replace "fglrx" with "ati":
sudo gedit /etc/X11/xorg.conf
Then restart.

Another option is to look in the /etc/X11/ directory for an older, backed-up version of your xorg.conf that isn't setup to use fglrx. Replace current xorg.conf with back up.

Okay, I changed it back to ati. However, the reason I changed to fglrx in the first place was that with ati, OpenGL rendering is
REEEEEEEALLY SLOOOOOOOOOW.
I'm talking like five FPS here. Which is kind of a bitch when you're trying to play Tremulous.

So, so far my options seem to be
(a) Have a working mouse
or
(b) Play 3D games.

Any other suggestions? :???:

EDIT: Oh yeah, I have an ATI Radeon Xpress 200M.

---

### Post by terrapin on 2006-07-21
I'm not sure if there are other options. I'm not an expert by any means.

For me, I don't play 3D games on my laptop because it's mostly for work/school...

I think a lot of other users are experiencing the same issues with this graphics card. Maybe a newer version of fglrx (when one is released) will fix it. Until then, do you have a PS/2 mouse?

---

### Post by hygraed on 2006-07-21
> **terrapin said:**
> I'm not sure if there are other options. I'm not an expert by any means.

For me, I don't play 3D games on my laptop because it's mostly for work/school...

I think a lot of other users are experiencing the same issues with this graphics card. Maybe a newer version of fglrx (when one is released) will fix it. Until then, do you have a PS/2 mouse?

You mean you're not a magical genius that can fix all my problems without once coming into contact with my PC? Well, damn!

Seriously, though, I wish I had a PS/2 mouse. Actually, I wish I had a PS/2 *port*.

---

### Post by el_escorpion on 2006-09-02
hmm, i'm experiencing the same problem. laptop, ATI Xpress 200M card and the same thing with the mouse. USB mouse, works after restart, then cuts out after a certain period of time. sometimes it can be a few minutes. Sometimes a few hours (if i restart and go into a game right away and stay there, tho it cuts off sometimes even there) And it ALWAYS cuts off when the screen goes slightly dark, for example when i enter synaptic or the shutdown menu.

---

### Post by webdr on 2006-11-29
Same here... although I hadn't thought of the video drivers causing the problem. Weird... ANYWAY... I hope there is a fix out there somewhere, I didn't have this problem with Dapper, and my other machines on Dapper don't have this problem either... hmmm perhaps I need to roll back to Dapper. Does anyone know of a good how to or FAQ for transferring all my email, settings, etc. ?

Thanks all!

---

### Post by webdr on 2006-11-29
Try adding noapic irqpoll pci=routeirq to the kernel line.
Worked  me...
;)

---

### Post by webdr on 2007-02-12
Updates to your kernel will cause this setting to be removed from the menu.lst file and you will need to re-enter the settings after kernel updates are performed.

so, I keep this thread book marked so I can easily return and copy / paste the string back into my mensu.lst file after kernel updates.

---

### Post by kanem on 2007-02-12
Hey that reminds me, I never thanked you for this fix in the first place. So thanks!

I find it's useful to keep a backup of all my important configuration files anyway so that I don't get stymied by new kernels and such.

---

### Post by lamalex on 2007-02-12
> **hygraed said:**
> Okay, I changed it back to ati. However, the reason I changed to fglrx in the first place was that with ati, OpenGL rendering is
REEEEEEEALLY SLOOOOOOOOOW.
I'm talking like five FPS here. Which is kind of a bitch when you're trying to play Tremulous.

So, so far my options seem to be
(a) Have a working mouse
or
(b) Play 3D games.

Any other suggestions? :???:

EDIT: Oh yeah, I have an ATI Radeon Xpress 200M.

strange, I have the same card with logitech G5 and I didnt have any problems using fglrx. I'm using ATi drivers now, i just dual boot windows solely for gaming but I had beryl with xgl and fglrx running for a while and my mouse worked great

---

