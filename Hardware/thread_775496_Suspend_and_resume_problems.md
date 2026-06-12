---
title: "Suspend and resume problems"
date: 2008-04-30
forum: Hardware
---

### Post by bogoliubov on 2008-04-30
Hello. I have a Clevo M540N laptop running Ubuntu 8.04. Most stuff works OK, but I have some strange problems with suspend and resume. 

If the laptop is running on AC power, I can suspend by selecting suspend in the menu. Sometimes it works by closing the lid, sometimes not. It seems that I have to close the lid slowly, but I'm not 100% sure of this.

Sometimes the computer reboots when putting it to sleep, I think it happens when closing the lid.

Sometimes the computer won't wake up from suspend. I think this happens most often when I've put it to sleep by closing the lid. When this happens, the computer makes a sound similar to that it makes when rebooting (I think it is the DVD drive), but the screen is black and I can't to anything except turning it off! The fan is running, so something has awaken...

Also, sometimes the computer wakes up, but the screen backlight is off. If I type in my password, it will light the backlight after a while. 


When on battery power, it won't sleep at all! I have no idea why.



I don't know what to look for in the kern.log or dmesg files, to see what the problem is. But I seriously need to have my laptop reliable when it comes to suspending! Any help is greatly appreciated!

---

### Post by bogoliubov on 2008-05-01
No one?

---

### Post by Frizguru on 2008-05-01
I am having the same problems on my laptop.

Dell Inspiron 5150
XGA Graphics Card

Ubuntun Hardy Heron 8.04

---

### Post by bogoliubov on 2008-05-01
> **Frizguru said:**
> I am having the same problems on my laptop.

Dell Inspiron 5150
XGA Graphics Card

Ubuntun Hardy Heron 8.04

All and the same problems?

---

### Post by bogoliubov on 2008-05-07
Does anyone know if the knew kernel (2.6.25) will solve this? I've read that it had fixes for many suspend/resume issues. But how would one go about installing it under Ubuntu?

---

### Post by reggie_mac on 2008-05-07
have you been through your power management options to check what it is doing, ie when you close the lid is it set to sleep or suspend? what battery level is auto shutdown? i was having some similar problems but by making sure i had the power settings the way i wanted them i've stopped those issues from happening.

---

### Post by bogoliubov on 2008-05-08
> **reggie_mac said:**
> have you been through your power management options to check what it is doing, ie when you close the lid is it set to sleep or suspend? what battery level is auto shutdown? i was having some similar problems but by making sure i had the power settings the way i wanted them i've stopped those issues from happening.

Yep, I have checked this and it's supposed to go to suspend when closing the lid. It actually goes to suspend sometimes, but not always, and it comes out of sleep horribly most of the time when I've closed the lid...

Thanks for your help though.

---

### Post by Kiri on 2008-05-08
I recently started having problems too. 
In the beta suspend was working pretty much fine when I closed the lid. Now since some update around the time final was released suspend never works anymore :(

---

### Post by schmolch on 2008-05-08
Dont worry, its normal that Suspend does not work, you are not doing anything wrong.

---

### Post by bogoliubov on 2008-05-09
> **schmolch said:**
> Dont worry, its normal that Suspend does not work, you are not doing anything wrong.

Yeah, I guess. But I want it to work! It doesn't have to come back from suspend fast or anything; but it has to be reliable! I think this is a major problem for all Linux distributions if we want Linux to become more popular.

---

### Post by reggie_mac on 2008-05-29
I'd say my suspend/resume works 50% of the time, and hibernate works correctly maybe 85% of the time. Still looking into the whats and whys of it, but it would be better if it just worked.

---

### Post by goombamd on 2008-05-29
I too am having this problem on the Dell m1330 .. very unreliable suspend and resume, hibernate and resume.  Usually have to reboot.

---

### Post by bogoliubov on 2008-05-30
This is a tricky problem, since there are so many different laptops out there. But it is the number one suggestion on the Ubuntu Idea pages...

For some reason; it now seems my laptop's suspend works OK, IF I suspend from the gnome menu; not if I close the lid! Actually, I can choose suspend in the menu, then close the lid after the laptop went into suspend. But it can be a problem waking up by opening the lid (as compared to pressing the power button).

---

### Post by i speak in math on 2008-05-30
My suspend works okay the first time. There are some oddities but overall, I can't tell much difference from a fresh boot. However, when I try to resume from the second suspend, my laptop completely locks up. No caps toggle or anything. I get a similar behavior with hibernate. (compaq c714nr)

---

### Post by pfeels on 2008-05-30
This fixed my desktop which stopped suspending after the latest kernel update, maybe it's a start or helps future troubleshooters 

turn back to the old kernel


Code:

sudo apt-get install startupmanager

Then go to System > Admin > StartUp-Manager

Default OS to > Ubuntu 8.04, kernel 2.6.24-16-generic

And your done

---

