---
title: "I can't format SD cards"
date: 2022-04-01
forum: Hardware
---

### Post by maxleod on 2022-04-01
I get this message when using Disks (gnome-disk-utility 3.18.3.1 UDisks 2.1.7):

Error synchronizing after initial wipe: Timed out waiting for object (udisks-error-quark, 0)

--*Ubuntu 16.04*

---

### Post by DuckHook on 2022-04-01
Ubuntu 16.04 is now EoL and has been for the past year.

It is highly unlikely that anyone here still runs it, so your version of Gnome Disks is too obsolete for us to reproduce. Without such reproduction, I for one cannot help you.

There have been huge changes since Xenial was released. One of those is the way Ubuntu now handles newer SD cards. For example, I believe that exfat is now part of the kernel. In Xenial, it was not. A current version could solve your issue naturally.

As a side note, running outdated versions is not just a danger to yourself, but a danger to the rest of us. Since it is now difficult to upgrade to a supported release, I would recommend that you back up your data and install from scratch. I don't know how much sense it makes to install Focal anymore. Jammy is already in beta and will be available as stable in less than 4 weeks. You may as well wait for that and get the benefit of two additional years of supported life.

---

### Post by maxleod on 2022-04-02
What do you mean "It'sa danger" to myself and everybody else? From Ubunutu.com:

[https://releases.ubuntu.com/](https://releases.ubuntu.com/)

> There are 2 types of Ubuntu releases: Interim and LTS. Each Ubuntu LTS  is maintained for 10 years total: 5 years of standard support + 5 years  of ESM. Interim releases are maintained for 9 months.

>             [h=1]These releases of Ubuntu are available[/h]     
                                 [h=3]Standard support[/h]                                                        [h=4]LTS Releases[/h]                 
[LIST]
[*][Ubuntu 22.04 LTS Beta (Jammy Jellyfish) &#8250;]("https://releases.ubuntu.com/jammy/")
[*][Ubuntu 20.04.4 LTS (Focal Fossa) &#8250;]("https://releases.ubuntu.com/focal/")
[*][Ubuntu 18.04.6 LTS (Bionic Beaver) &#8250;]("https://releases.ubuntu.com/bionic/")
[/LIST]
               
                                [h=4]Interim Releases[/h]                 
[LIST]
[*][Ubuntu 21.10 (Impish Indri) &#8250;]("https://releases.ubuntu.com/impish/")
[*][Ubuntu 21.04 (Hirsute Hippo) &#8250;]("https://releases.ubuntu.com/hirsute/")
[/LIST]
               
             
           
         
                    [h=3]Extended Security Maintenance (ESM)[/h]           
[LIST]
[*][Ubuntu 16.04.7 LTS (Xenial Xerus) &#8250;]("https://releases.ubuntu.com/xenial/")
[*][Ubuntu 14.04.6 LTS (Trusty Tahr) &#8250;]("https://releases.ubuntu.com/trusty/")
[/LIST]
         
       
     
   

Even 14.04 Trusty Tahr still gets security updates.

---

### Post by ajgreeny on 2022-04-02
> **maxleod said:**
> What do you mean "It'sa danger" to myself and everybody else? From Ubunutu.com:

[https://releases.ubuntu.com/](https://releases.ubuntu.com/)

Even 14.04 Trusty Tahr still gets security updates.
But only if you have registered and signed up for it.

Have you done so?  If not you are a danger to the whole community!

---

### Post by DuckHook on 2022-04-02
> **ajgreeny said:**
> But only if you have registered and signed up for it.
+1

@maxleod

You need to have signed up for Canonical's ESM service. If you don't remember doing that, then your version went out of support last year. You can also tell if you are still covered simply by noting whether you are still getting updates or not.

For the lurkers out there:

We live in a pretty sad security landscape these days. Security holes, some of them of scary severity, are discovered pretty much daily. Kernel patches are pushed out weekly or biweekly. Letting upgrades go for, say, a year is equivalent to dangling the keys to your front door on a hook by the lamp post for a year with a big sign advertising your address. Only, in the case of computers, the bad guys don't just break in&#8212;they take over your basement/attic and use it as their base for further break and enters throughout the rest of the neighbourhood.

It's a stretched analogy, but a valid one.

---

