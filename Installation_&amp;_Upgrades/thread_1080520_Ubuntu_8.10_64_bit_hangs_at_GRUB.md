---
title: "Ubuntu 8.10 64 bit hangs at GRUB"
date: 2009-02-25
forum: Installation &amp; Upgrades
---

### Post by EvilPeppard on 2009-02-25
Hello all. I am new here, so I hope you all are doing well.

I've just removed all the partitions off my Dell Optiplex 755 that had Vista on it and Installed Ubuntu 8.10 64-bit (I have 4GB of RAM). The installation went fine, but when my system reboots after the install, my machine hangs at the word GRUB. The system does have a RAID 1 configuration in it.

I am very new to Linux systems, hence why I went for Ubuntu. Could you please assist me as to why my system will not boot past this point? I have installed Ubuntu 8.10 32-bit on other machines with no problem.

I've searched these forums some, but didn't find anything solid during that time.

Thank you for your time and assistance.

---

### Post by caljohnsmith on 2009-02-25
You normally have to take special steps to install Grub to a RAID setup:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Let me know if that works for you or not.

---

### Post by EvilPeppard on 2009-02-25
> **caljohnsmith said:**
> You normally have to take special steps to install Grub to a RAID setup:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Let me know if that works for you or not.
Thanks. I'll look at this and report back.

---

### Post by EvilPeppard on 2009-02-25
> **caljohnsmith said:**
> You normally have to take special steps to install Grub to a RAID setup:

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

Let me know if that works for you or not.
Wow. I'm dizzy from all the info there. It looks complex.

Would it just be easier to break my RAID and have two individual drives set in the BIOS, then install Ubuntu?

---

### Post by caljohnsmith on 2009-02-25
> **EvilPeppard said:**
> 
Would it just be easier to break my RAID and have two individual drives set in the BIOS, then install Ubuntu?
Absolutely it would be easier. That's what I would do if I were in your shoes, because I wouldn't want to mess with RAID either. :)

---

### Post by EvilPeppard on 2009-02-25
> **caljohnsmith said:**
> Absolutely it would be easier. That's what I would do if I were in your shoes, because I wouldn't want to mess with RAID either. :)
Ok, I will break the raid and see how it goes.

Thanks for the info. :)

---

### Post by EvilPeppard on 2009-02-25
I broke the raid config and let Ubuntu install to a single drive and it worked great.

Thanks again for all the help.

---

### Post by caljohnsmith on 2009-02-25
Glad to hear you were able to successfully install Ubuntu; cheers and have fun with your new Ubuntu install. :)

---

