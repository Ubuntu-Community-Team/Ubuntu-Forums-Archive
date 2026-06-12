---
title: "hibernating issue: pat entry 2..?"
date: 2008-05-02
forum: Hardware
---

### Post by amirman on 2008-05-02
ok, this isn't very serious since hibernation is not totally broken, just slightly, but when i hibernate my laptop it goes to a screen with text that says:

> random numbers.random numbers [fglrx: KCL_Enable_Pat] *ERROR* Pat entry 2 is already configured

this may not be exact but it's basically what it shows, then it waits for about 40 seconds and shuts down. it's not that big of a deal because when i start back up i have to go through grub and everything but it *has* saved my desktop session, but it shouldn't be sending me back through grub and everything, right?

sometimes the screen where the message shows has this white grid over it and the text is garbled but everything else happens the same way.

any ideas? what's a pat entry?

i've tried deleting my windows hibernation file and turning hibernation off in windows (i'm dual booting) but that doesn't change anything.

thanks

---

### Post by excogitation on 2008-05-20
Did you find a solution to this problem?

---

### Post by amirman on 2008-05-20
> **excogitation said:**
> Did you find a solution to this problem?

no :(
if you wait on that screen long enough, it hibernates, but you have to go through Grub to bring it back up, i guess the main downside is that it takes so long to hibernate and to bring it back up when it should take just a matter of seconds. I just wish someone would enlighten me as to what a Pat Entry even is.

:confused:

---

### Post by excogitation on 2008-05-20
I get the same error message when trying to hibernate, but I can't even resume through grub.

uswsusp (s2disk) works better on my machine - but not as good as wanted.

---

### Post by amirman on 2008-05-20
> **excogitation said:**
> I get the same error message when trying to hibernate, but I can't even resume through grub.

uswsusp (s2disk) works better on my machine - but not as good as wanted.

suspending works almost perfectly on my machine though i get the occasional error with something when i wake it.  What machine are you using? i'm on a Dell Inspiron E1505 laptop.

---

### Post by excogitation on 2008-05-20
I'm using it on an Acer TM8106wlmi and I'd really like Hibernation to work :-)
(and some other things).

At the moment I'm thinking of buying a new Laptop but I don't have too high expectations that there will be less problems with a new Computer.
Maybe in a few years :(

---

### Post by wahoobob on 2008-05-22
I'm having the same issues with a Thinkpad T42p.  I wonder if there is a bug report to follow?

---

### Post by excogitation on 2008-05-22
> **wahoobob said:**
> I wonder if there is a bug report to follow?

[Well there is now.]("https://bugs.launchpad.net/ubuntu/+bug/234125")

Feel free to contribute ;-)

---

