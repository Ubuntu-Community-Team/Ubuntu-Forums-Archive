---
title: "Shutdown"
date: 2005-05-13
forum: Hardware &amp; Laptops
---

### Post by rnewby52 on 2005-05-13
I love Ubuntu and it runs well on my Dell Inspiron 2500 but, it shuts down on it's on with no warning.  I'll be using it on the net or playing a game and all of a sudden it shuts down.  It's just like I turned it off with a switch.  I want to continue using it but I need to resolve this problem.  Does anyone have any ideas.

---

### Post by TheOtherShoe on 2005-05-13
My laptop used to switch off without warning when I first installed Gentoo. The problem was that it was that the fan was not turning on because I had ACPI configured incorrectly and so my laptop was overheating.

So if your computer is switching off when you are doing something processor intensive and you never hear the fan come on, that might be your problem. If you can't get ACPI support configured correctly then disabling it should allow your fan to work properly; IIRC you can disable ACPI by adding the line ACPI=off to your grub options.

Also, a friend of mine just told me that he had similar problems with his desktop when due to a dead graphics card and another occasion because the onboard sound was dead, so these are also things to check out.

Hope this was helpful.

---

