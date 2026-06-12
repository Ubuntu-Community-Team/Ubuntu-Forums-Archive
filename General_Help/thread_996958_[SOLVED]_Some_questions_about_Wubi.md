---
title: "[SOLVED] Some questions about Wubi:"
date: 2008-11-29
forum: General Help
---

### Post by Deep Blue on 2008-11-29
Hey there everyone. I'm wanting to go back to Ubuntu, but I would like to keep Windows as well. Currently, I'm dual booting XP and Vista. 

Should I:

A) Install Wubi (can remove whenever I like, boots normally through GRUB, should retain the option of booting to Windows, GRUB removed when Wubi removed?)

B) Install through Alternate/ LiveCD.

Thanks a lot!
Niko.

EDIT: What are the performance hits of Wubi?

---

### Post by oilchangeguy on 2008-11-29
> **Deep Blue said:**
> Hey there everyone. I'm wanting to go back to Ubuntu, but I would like to keep Windows as well. Currently, I'm dual booting XP and Vista. 

Should I:

A) Install Wubi (can remove whenever I like, boots normally through GRUB, should retain the option of booting to Windows, GRUB removed when Wubi removed?)

B) Install through Alternate/ LiveCD.

Thanks a lot!
Niko.

EDIT: What are the performance hits of Wubi?


this needs to be posted in main support, wubi.

---

### Post by mikewhatever on 2008-11-29
Actually, I don't see a question about wubi here. The question is rather which installation way to choose, and the answer is, it doesn't matter. You can get similar setups both ways.

---

### Post by w4ett on 2008-11-29
> EDIT: What are the performance hits of Wubi?

Wubi, runs well on MOST installs, but you are somewhat hampered by running it within windows (depending on the amount of ram that you have available).

With your current installation I'd recommend dropping in another Hard Drive and doing a clean install on it. At the current prices of hardware (dropping daily) there is little reason not to add another drive.  This will enable you to keep your windows dual boot install completely separate from Ubuntu.  You can even use the KISS method for install...unplug your windows drive and install on the new drive only and then use your boot options on boot up to select the hard drive you would like to boot from.  This keeps grub from interferring with your windows MBR.

Just my 2 cents..

Good Luck

---

### Post by Paqman on 2008-11-29
> **w4ett said:**
> Wubi, runs well on MOST installs, but you are somewhat hampered by running it within windows (depending on the amount of ram that you have available).


What? That's not true at all. Wubi is not a VM, no part of Windows is loaded into RAM when you're in Ubuntu. 

The actual disadvantages of Wubi are:
[LIST=1]
[*]You cannot use hibernation
[*]It doesn't like power outages. If you think there's any chance that the power will fail, don't use Wubi. Obviously this is never a problem on laptops, as they have a battery and will shut down gracefully if it runs flat.
[*]Unless you install Wubi from the LiveCD, you won't be able to test your hardware before installing.
[/LIST]

So if none of those are a big issue for you, Wubi is a good option.

---

### Post by Deep Blue on 2008-11-29
> **oilchangeguy said:**
> this needs to be posted in main support, wubi.Okay, I reported my post and asked for a move. :)

> **mikewhatever said:**
> Actually, I don't see a question about wubi here. The question is rather which installation way to choose, and the answer is, it doesn't matter. You can get similar results both ways.Okay, I was actually wondering is:

When I remove Wubi (just good to know; I probably won't), I will also lose GRUB and return to the default boot manager(?). 

Also, can I install Wubi on say D:\\ instead of C:\\?

Thanks again.

---

### Post by w4ett on 2008-11-29
> What? That's not true at all. Wubi is not a VM, no part of Windows is loaded into RAM when you're in Ubuntu.

Sorry maybe I should elaborate :wink:

I've had some trouble installing wubi on low ram systems 128-256 Mb...just didn't seem to load properly..but found that a clean, full install just worked better.

---

### Post by mikewhatever on 2008-11-29
> **Deep Blue said:**
> 
Okay, I was actually wondering is:

When I remove Wubi (just good to know; I probably won't), I will also lose GRUB and return to the default boot manager(?). 

Also, can I install Wubi on say D:\\ instead of C:\\?

Thanks again.

I believe most of the questions are answered, and in more accurate way, in the wubi FAQ.[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php) I've never used wubi myself, so can't advise.

---

### Post by Deep Blue on 2008-11-29
> **w4ett said:**
> Sorry maybe I should elaborate :wink:

I've had some trouble installing wubi on low ram systems 128-256 Mb...just didn't seem to load properly..but found that a clean, full install just worked better.Naw, I got 2 gigs, should be fine. ;)

> **mikewhatever said:**
> I believe most of the questions are answered, and in more accurate way, in the wubi FAQ.[http://wubi-installer.org/faq.php](http://wubi-installer.org/faq.php) I've never used wubi myself, so can't advise.Thanks very much, answers my question and looks simple enough, and Joy for using the Windows boot manager.

---

