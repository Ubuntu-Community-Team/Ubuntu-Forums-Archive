---
title: "debugging power suspend mode"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by bobhenz on 2007-12-14
Back-story:

I assembled a desktop computer about a year ago and installed Ubuntu on it using the money I saved on software to upgrade my hardware. I've been very impressed. But there have been a couple problems that have been there since the beginning and still persist for me since Dapper all the way up to Gutsy (which I'm currently running). I am now being proactive and going to try to debug one of those problems.

Problem:

Suspend and Hibernate have never worked. (Should they work on a desktop?) Since I assembled this computer myself the first thing I am uncertain about is... the hardware. Perhaps I didn't connect a certain wire or enable a special BIOS setting (I've twiddled with them pretty extensively without any luck).

When I choose "suspend" from the shutdown/logout window, the computer does go to sleep I think because the power light blinks instead of being on steady or completely off. However no amount of mouse clicking or key pounding will get my computer to awaken again.

Step 1:

So I would like to try a bare-bones approach, boot to a prompt (so that video driver doesn't load), type some magic command, watch my computer go into "sleep mode" then hit a key and have it come out. (Remember I want to verify that the hardware CAN go to sleep and wake up again.)

So let's break this down totally. Up to this point I have been strictly a "user" of Ubuntu. I'm a programmer and use linux at work, but the IT guys take care of problems like this plus they're running Red Hat so whatever.

Step 1a: Boot to a prompt. How do  I do this? Is this just chosing "recovery mode" from the Grub menu?

Step 1b: Type a command to put the computer into sleep mode. Is there a command-line command to do this? If so what is it?

Step 1c: Now I need to wake it up. Are there BIOS settings I need to look for? Not really looking for exact setting text (since you have no idea what BIOS code my system has), just really verification that "Yes there is usually a BIOS setting to *blah*."

I have an ASUS motherboard and I noticed that there is a "Power on from PS2 keyboard press" which is currently disabled. (Yes I did try enabling this before I started this post and still couldn't wake up my computer but that is with a full logged-in boot so...) But that says "power on" and I'm really just wanting to "wake up".

Any help with any of these 3 baby steps would be GREATLY appreciated.

Thanks in advance,
Bob

---

### Post by bobhenz on 2007-12-17
Well, I'll answer my first question. It looks like if I boot recovery mode I get to a prompt and I'm logged in as root?! That doesn't seem very secure... but that's not my issue right now.

So now I have a terminal and the video driver hasn't been loaded (as far as I can tell). So can anyone answer step 1b?

---

### Post by sinpalabras on 2007-12-21
No i can't answer that, but i'm having the exact same problem, so i'll keep searching and tell you if i find something

---

### Post by cuervo73 on 2007-12-21
running Ubuntu 7.10 here on a 6 y/o Toshiba Satellite...  

yesterday, I tried <suspend> and it shutdown and powered-off.  Today, when I restarted it, it "resumed" just fine except, my wireless connection was down and I had to reconnect.  Otherwise, everything on the desktop was exactly as I left it yesterday.  I'm happy.

cuervo

---

### Post by cuervo73 on 2007-12-21
I beg your pardon..  what I just posted was WRONG.

what I said was, "...Yesterday, I tried <suspend>...

when what I meant was "Yesterday, I tried <Hibernate>...

Hibernate does restore the state of the machine/Ubuntu.  after power-on and grub
menu, chosing Ubuntu, and after all restoring, I see the lockscreen panel asking me for a password.  The desktop then comes up as if nothing was done.

When I tried <suspend>, it shuts off like I said, but upon resume, the
video is hosed up.. it is black-on-black.  However, everything is still running,
and I can remotely login to Ubuntu using ssh from another box.  I also
can get an idle "getty" via <Ctrl><Alt><F2> and login as root and type:
shutdown -r now.  There is no video, so you have to be careful as you
type, lest you make a typo which you cannot see..  :^)

But, Hibernate works just fine

cuervo

---

### Post by bobhenz on 2008-01-19
:(So no one is going to help me with my baby steps? I'm glad you other people are having some marginal sucess but I'd really like to get this debugged on my system.

Any gurus out there want to help?

---

### Post by fraia on 2008-03-04
I use

sudo /etc/acpi/sleep.sh sleep

to put my laptop into suspend, i use it all the time. The equivalent for hibernation:

sudo /etc/acip/hibernate.sh hibernate

will kill X but the machine hangs, i never use it - just tried it to check and had to do a hard reboot.

'acpi' is the power management protocols, i dont' know if they're installed by default on a desktop machine (my guess would be yes) but if the scripts are not in /etc/acpi/ then you may need to re-configure your kernel

---

### Post by mdshann on 2008-03-05
As far as I know ACPI support is still being worked on at the kernel level and does not yet work perfectly. I never use either mode even when in Windows because they don't always work correctly. They are both good features to have if you are always on the go and want to have your system back up quickly without loosing work, but even in the Windows world they are not perfect. :(

---

