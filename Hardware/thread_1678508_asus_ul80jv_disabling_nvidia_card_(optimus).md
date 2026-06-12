---
title: "asus ul80jv disabling nvidia card (optimus)"
date: 2011-01-30
forum: Hardware
---

### Post by szymzet on 2011-01-30
So I have this laptop which uses optimus technology, which isn't supported on linux. I didn't install the properitary drivers, but the card is still running alongside the intel card and eats up my battery. I don't want to use it on linux, but I don't know how to disable it. I tried to use acpi_call, but I am quite a noob when it comes to linux, so I probably did something wrong as it did't work. Can anyone give me a step by step guide on how to disable the dedicated nvidia card? cheers

laptop spec : asus ul80J series, model ul80Jv, 1.2GHz core i3, nvidia geforce 310m + intel integrated card (optimus techonology)

---

### Post by szymzet on 2011-01-31
Hmm, nobody solved it? Maybe with a different laptop? Anyone...?

---

### Post by asdir on 2011-01-31
Does [that]("http://ubuntuforums.org/showthread.php?t=1470822") maybe help you?

It is not quite what you wanted, but it sounds like it could help...
At least the guy in this thread seemed to be ok with the solution in the end.

---

### Post by ng0ofy on 2011-02-11
> **asdir said:**
> Does [that]("http://ubuntuforums.org/showthread.php?t=1470822") maybe help you?

It is not quite what you wanted, but it sounds like it could help...
At least the guy in this thread seemed to be ok with the solution in the end.

Yes!*They*make*the*workable*things*to*working.*BUT*We*want*to*this*working*things*disable!

So,*any*solution,*to*DISABLE*NVIDIA*GRAPHIC*CARD*in*OPtimus*technology*ready*notebooks*for*Ubuntu?

---

### Post by marcussive on 2011-04-07
This is targeted to a specific model: [http://ubuntuforums.org/showthread.php?t=1677780](http://ubuntuforums.org/showthread.php?t=1677780)
Not surprisingly, it did not work for me (Asus N53JF). I then found this, which might be of some use to you: [http://ubuntuforums.org/showthread.php?t=1677780](http://ubuntuforums.org/showthread.php?t=1677780)
I am new to linux and have not figured it out yet.

---

### Post by beew on 2011-04-07
Please add your voice here. [http://ubuntuforums.org/showthread.php?t=1712278](http://ubuntuforums.org/showthread.php?t=1712278) 

With Optimus basically Nvidia has stopped supporting Linux laptops because you cannot use the Nvidia card you paid for **at all**. The card may have Linux driver but it won't work if Optimus is enabled,--and worse than not working because it will continue to generate heat and eat your resources. 

This is  very serious for Linux laptop users who want good graphic support because almost all newer laptops with Nvidia comes with Optimus enabled and sometimes they don't even tell you and that can mean the end of Nvidia for Linux laptops.  I don't expect Nvidia to support Optimus for Linux but they should provide a way to allow Linux users to use the chip without gpu switching, which Nvidia supports by providing Linux driver!

---

### Post by beew on 2011-04-07
> **ng0ofy said:**
> Yes!*They*make*the*workable*things*to*working.*BUT*We*want*to*this*working*things*disable!

So,*any*solution,*to*DISABLE*NVIDIA*GRAPHIC*CARD*in*OPtimus*technology*ready*notebooks*for*Ubuntu?


Take a look at this .
[URL="http://ubuntuforums.org/showthread.php?t=1657660&page=3"]
http://ubuntuforums.org/showthread.php?t=1657660&page=3 [/URL]

---

