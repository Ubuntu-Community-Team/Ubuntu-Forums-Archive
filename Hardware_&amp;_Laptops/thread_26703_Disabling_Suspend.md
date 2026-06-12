---
title: "Disabling Suspend"
date: 2005-04-13
forum: Hardware &amp; Laptops
---

### Post by iogiuseppe on 2005-04-13
In searching through the forums I've seen many posts related to *enabling* suspend or fixing suspend related problems related to lid closing.... but I'm actually trying to do the opposite. 

My goal is to find out how to configure my laptop to NOT suspend when the lid is closed.  I, of course, want it to shut off the screen to save battery and eliminate a source of heat, but I don't want the laptop to suspend or lock or anything. 

How can I accomplish this? 

I'm using a fresh install of 5.04 on a Dell C610 - but will want this available for all machines I load it on.

---

### Post by Laurent Cazalet on 2005-04-14
Ciao!
Are you using APM or ACPI. On my C600 I use APM.

With APM, I would look in the bios setup. 
With ACPI, take a look in the /etc/acpi directory, and find the lid event handler. It should be a script, that you can edit as root in order to change what to do when the system is notified that the lid was opened/closed. 
Take a look at the bios setup anyway.

---

### Post by iogiuseppe on 2005-04-18
Yep, worked like a charm. 

At first, I was a bit daunted, in that I've no idea what edits I should make to a file like that ... not even sure what my options were. 

Then it dawned on me: Just comment everything out :)

Now, since my lid is closed (I'm using the machine via VNC) I'm not sure if the screen is off or not ... But as for right now, I'm satisfied. 

I'll look into making sure the screen is shut off now. 

Any hints? 

Joe

---

### Post by kluut on 2005-04-18
xset dpms force off
turns off the screen. So you could try putting this in the script in which  you commented everything out.

---

