---
title: "toshiba M55 power off works w/o external mouse, but acts up with one"
date: 2006-03-03
forum: Hardware &amp; Laptops
---

### Post by geocritter on 2006-03-03
Hi everybody,

Can somebody give me a hand with this?  I have breezy installed on my Toshiba Satellite M55-S3314, and it's working great, including acpi stuff.  Except one thing.  When I hook up a usb optical mouse (microsoft), it works fine, until I go to power off.  The system goes down, the screen goes blank, but the computer won't turn all the way off.  But if I don't have the mouse plugged in, it powers off just fine.

Any thoughts or workarounds?

Thanks,
Dan

---

### Post by jniebles on 2006-05-06
Hi all,

Dan, I have the same problem on the Toshiba Satellite M55-S325.
Have you found any solution/suggestion??

Thank you,

JuanCarlos

---

### Post by jniebles on 2006-05-06
By the way, this is the output that I am getting when typing *acpi -V*

juancarlos@davinci:~$ acpi -V
     Battery 1: charged, 100%
No support for device type: thermal
  AC Adapter 1: on-line

Does it mean that acpi is not working properly?

Thnx,

JuanCarlos

---

### Post by geocritter on 2006-05-06
I found that it was the same with Suse and FreeBSD, both.  I don't think it's so much related to ACPI from the OS as it is something goofy coming out of the bios, where it doesn't seem to want to "release" the usb port or something.  I dunno...but it doesn't seem to be a big problem.  I just use the power button to shut it off after the OS finishes shutting down.  Maybe someone else might have a clue?

On your output, I've seen that as well.  I don't think that's an issue; just the fact that our machines I don't think have the capability to report the thermals...

Again, I could be wrong...

---

### Post by jniebles on 2006-05-08
Thank you Dan for your answer. Since it seems you are still running Ubuntu on this machine, I have two more questions for you.
 - Does your Hibernate works? mine doesn't...
 - I installed the network-manager package, have you tried it? Now I'm getting an error message after logging in to Gnome about some "link detection" not supported by the wired network card. Have you experienced this?
I appreciate your help.
Thnx,

JuanCarlos

---

### Post by Mikecore on 2006-05-08
I cant get my acpi to work on my M55 S329 do you have a link to a good tute?

---

### Post by Tom Tiger on 2006-05-09
There is a little trick on the newer toshiba systems that might cause this, but it is a long shot (I havent got an M5x series in so I can't test or replicate what happens)  

There is a mouse shortcut hardwired in the bios,  FN+F9  this turns the mouse 1 off, mouse 2 on, both mice on, both mice off (it cycles) BUT when you restart the toshiba it remebers the last setting. It could be that you'll have to play with this keycombination and see what happens.

But it's a long shot...

:-k

---

