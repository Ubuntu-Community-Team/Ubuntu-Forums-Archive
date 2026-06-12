---
title: "Mouse on KVM &quot;goes crazy&quot; when switching to Ubuntu"
date: 2008-09-30
forum: Hardware
---

### Post by nemesis256 on 2008-09-30
I've got a Ubuntu computer connected to a KVM, and every time I switch to it, the mouse jumps around VERY quickly, and clicks by itself.  If I leave the mouse there for about 30 seconds, it's fine.  It also becomes fine after the same amount of time if I move the mouse around, but there may be new folders, new or deleted panels, etc.  The mouse connected on the KVM is PS/2.  Any ideas?

---

### Post by nemesis256 on 2008-10-01
anyone?

---

### Post by neonprophet on 2008-10-07
I get the same thing, except mine just randomly starts moving horizontally all over and clicking. Usually it begins with a click on a windows top bar or a button. 5-30 seconds later it just stops but it results in missing/moved things, bars deleted, totally random.

---

### Post by stekker on 2008-10-20
I had the same problem, I'm running hardy.
normally the mouse gets autodetected but a kvm-switch spoils a lot so the best you can do is not autodetecting but forcing the mouse-module in the mode that it needs.


try this from the commandline:

echo options psmouse proto=imps >options
sudo cp options /etc/modprobe.d/

for me it worked perfectly.
my imps (IMproved PSmouse) is a (USB) logitech trackman wheel that is connected via USB->PS/2 adaptor to a low budget StarTech KVM.

If you happen to have a mouse with more than 3 button + scrollwheel like, say, a mouse with extra thumb buttons you could also try this:

echo options psmouse proto=exps >options
sudo cp options /etc/modprobe.d/

hope it helps :-)

---

### Post by zaazz on 2010-08-10
I tried both of the below commands in the terminal but it still hasn't resolved my issue. 

> echo options psmouse proto=imps >options
sudo cp options /etc/modprobe.d/

echo options psmouse proto=exps >options
sudo cp options /etc/modprobe.d/



As described in the first two posts when I change back to my ubuntu 10.04 PC via the KVM switch the mouse goes crazy for like 10-30 seconds. If I move it at all it jumps all over the place and clicks on things even though I'm not pressing either button on the mouse. If I don't move it at all and just wait it sometimes resolves its self without having a bunch of extra windows I need to close after regaining control of my pointer.

Lately, another issue that's been happening, after I regain control of the mouse I lose my ability to left or right click on things and then I need to reboot.

I had this same problem with previous versions of ubuntu and it forced me to stop using the system with my current setup. I need to be able to use this switch to work with my different computers at work and I don't want to put in a PO to get a new switch only to find out it didn't solve the issue. The ubuntu system is the only one who has this issue.

Any other fixes out there?

---

