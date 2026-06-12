---
title: "Ubuntu doesn't like my chipset"
date: 2006-03-13
forum: Hardware &amp; Laptops
---

### Post by stickninja on 2006-03-13
Okay, so I am trying to install Ubuntu on my new server. The motherboard I have is an Asus P5DC-MX with the VIA 8251 South Bridge. After lots of research, I have discovered that VIA's 8251 South Bridge is not supported under the current kernels (2.6.x.x). I've tried both 5.10 and 6.04, but neither of them will recognize my SATA Hard Drives, because they are unable to talk to the South Bridge. There is a long thread on VIA Arena about this, and basically what it comes down to is there is a patch that may or may not work, and better support is coming in future kernel revisions. Unfortunately, I'm a newbie at Linux, and my skill level is not high enough yet to go and try patching the kernel. However, I need this server running soon, so I was thinking of getting an add-on SATA card and using that until the kernel becomes updated in the main tree. My question (sorry it took so long to get there) is: can I boot from hard drives connected to a PCI controller card? Thank you for any help you can provide.

---

### Post by bb002 on 2006-03-14
I personally haven't done this so I can't be for sure but you should be able to. I believe in the past there weren't (is that a word?) any onboard IDE and such, it all came as an add-on card. Now the add-on card has simply been intergrated into the actual MB. So in a way you have always booted from a PCI card.

On my MB I have an option to set the boot device to a "Other Boot Device". No idea if that's your PCI card or not.

Only sure way is to try it. SATA PCI card are pretty cheap aren't they? I've seen them range from $15 to $35 dollars. I'd asck someone at the store what the return policy is if it is incompatible with your system and get their policy don't let them convince you otherwise. I made that mistake once.

---

### Post by el3ktro on 2006-03-14
Yes this should work, as long as you can select this additional SATA card in the BIOS to boot from. Well, unfortunately Linux and VIA are like cats & dogs - they really don't like each other. Honestly, I had so many problems with VIA under Linux, if you're really into Linux and want to do serious stuff with it, get a new mobo - that will preserve you from some sleepless nights trying to get this damn VIA thing to work. You can get new mobos (NForce) for example for around 40€, so thats really not it.


Tom

---

