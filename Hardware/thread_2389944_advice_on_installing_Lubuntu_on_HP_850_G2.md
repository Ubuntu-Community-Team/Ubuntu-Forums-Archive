---
title: "advice on installing Lubuntu on HP 850 G2"
date: 2018-04-23
forum: Hardware
---

### Post by ardouronerous on 2018-04-23
Hello, my cousin works for a company (which I cannot name) and they were in the middle of a software and hardware upgrade, so instead of throwing the hardware away and contributing to ewaste, they are giving away old laptops, CPUs, monitors, printers, scanners, etc to their employees.

Anyway, my cousin got 3 laptops, all the same model, a 2015 HP EliteBook 850 G2 and is going to mail me one of the laptops. The laptops and CPUs were given away without their HDDs and SSDs, so I  have to buy an SSD for this laptop, which is understandable because they  could contain sensitive company information. 

I have never installed Lubuntu on a UEFI laptop before, so I need some advice. I heard it's simpler to disable UEFI and enable legacy boot.  As I said, I need some advice, thanks.

---

### Post by Autodave on 2018-04-24
That should be an i5, 2.2 (2.7 turbo) with 4 gig of RAM. You could run Ubuntu or Xubuntu: you really don't have to go as simple as Lubuntu.  And, if you put an SSD in there, it will be quite fast.

After installing your HD, turn the computer on and immediately start hitting the ESCAPE key. That will bring up a screen with several boot options: press F10 to get into the BIOS. Realize at this point that your mouse pad will be inop: you will have to use the arrow keys. Now you need to navigate to where you disable UEFI. I can't remember exactly what screen that is on, but usually something like Administration, Safety, or such. Just look through and you will see it: it is quite obvious and is not hidden.

While you are in there, on either the first or second screen: make sure that "Boot from USB" is enabled if you want to do it that way, or if you are going to use a DVD, make sure that is also there.

---

### Post by ardouronerous on 2018-04-24
Thanks for the reply :)

This is what I've found:

[IMG]https://support.hp.com/doc-images/676/c03980378.jpg[/IMG]
[IMG]https://support.hp.com/doc-images/355/c04682586.jpg[/IMG]

The Secure Boot option is found under System Configuration -> Boot Options.

So, just for clarity, I should disable Secure Boot and enable Legacy Support?

---

### Post by Autodave on 2018-04-24
Correct.

Realize this: 18.04LTS will be released in 2 days. You may want to wait for that, or you can go ahead with your 16.04LTS which will be maintained for at least 3 more years.  I have see where 18.04 will be able to be booted in UEFI mode, but that is all that I know. Perhaps someone else will chime in here and educate both of us. :-)

---

### Post by ardouronerous on 2018-04-24
Thanks for the clarifications.
I prefer Lubuntu because I've been using it for a longtime now, it's become a personal choice for me lol.

On upgrading to 18.04 LTS, it's been my experience that first LTS releases are always buggy, so it's best to wait til 18.04 becomes 18.04.1, so I'll probably upgrade next year.

Yeah, HP EliteBook 850 G2 doesn't come with a CD/DVD drive, so I'll be installing Lubuntu via USB, so based on the image above, which should I select on Legacy Boot Order?

USB Diskette on Key/USB Hard Disk or USB CD/DVD ROM Drive?

---

### Post by Autodave on 2018-04-24
USB Diskette on Key/USB Hard Disk

---

### Post by ardouronerous on 2018-04-25
Okay thanks :)

I'll bookmark this thread and update when I've installed Lubuntu on the laptop, my cousin is still on the process of mailing it to me.

---

