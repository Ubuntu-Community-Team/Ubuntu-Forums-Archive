---
title: "Upgrading from R9 280x to Nvidia - which board to buy?"
date: 2017-07-01
forum: Hardware
---

### Post by onlineguy on 2017-07-01
Hi,

currently I'm running 16.04.1 with a R9 280 X graphics boards. I made the decision to stay on LTS because I want to have a hazzle-free environment since I lack time to take care of that and because I want a stable programming environment. Exception is oibaf ppa for updated mesa. Besides that, I frequently run a game or two (Paradox Interactive games and War Thunder).

For various reason I need CUDA support in near future so I will have to make a move to Nvidia. So my question is: which Nvidia board should I buy to...


[LIST]
[*]- ...have minimum install effort (MUST; I do not want to follow pages and pages of shell commands to make a hack) 
[*]- ...have minimum maintenance effort (MUST; I do not want to fix the system after every graphics driver or kernel update) 
[*]- ...be able to stay on 16.04 (OPTIONAL; reduce risk of breakage, HWE could be an option) 
[*]- ...have improved gaming performance (OPTIONAL; I do not want to become slower by upgrading) 
[/LIST]

---

### Post by Autodave on 2017-07-01
I have never had a problem with Nvidia cards in anything. Install the card, boot the machine, go to *Additional Drivers* and install the recommended driver. Reboot.

I currently have a 1/2 G, one G, and a 4 G card running in 3 different machines: all on the "recommended" driver. All on 16.04.

As far as which specific board to buy, that depends on your wallet more than anything. :-)

I am sure that a few others will jump in here with their personal favorites, but any newer Nvidia card should be a snap to install and get running quickly.

---

### Post by onlineguy on 2017-07-01
> **Autodave said:**
> ...I currently have a 1/2 G, one G, and a 4 G card running in 3 different machines...

Can you elaborate on this, please? I guess you are talking about chip generations, which 4G cards do you have?

---

### Post by Autodave on 2017-07-01
My 4G card is a GT740.

What I am saying is that support for Nvidia is excellent on Ubuntu. Unless you are looking at a 3 year old or much older card, you will have no problems getting the proper for you card.

I do know that there are extra programs/drivers for the Cuda portion programming and I am not familiar with those.

---

### Post by efflandt on 2017-07-02
Last I heard Nvidia has best support for Linux graphics drivers, especially for Steam games. I had a GTX 550 Ti when Linux Steam was still beta in Ubuntu 12.04, to GTX 750 Ti in 14.04 (nouveau did not support it yet, so I had to install nvidia drivers from recovery boot) which was mostly faster using half the power, to 3 GB GTX 1060 currently. That works fine for my single 1080p display which normally uses about half of its VRAM in games (6 GB models would be better for 1440p). There are other GTX models up from there, but my OEM PSU only has (1) 6-pin power connector and even some GTX 1060 models use 8-pin.

If you need or want a newer driver than is in the repos, you can add the graphics-drivers ppa [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa) then **Additional Drivers** should give you additional choices (currently up to nvidia-381).

Support for cuda is added separately which is easiest to find/install using **synaptic** package manager. There is a way to test if cuda is working and it was. If using cuda for blender I heard that (and actually did) run blender once as root (sudo) to enable cuda, after that you can use cuda in blender as a normal user. But I could not figure out how to get cuda to work when using blender indirectly from Openshot Video Editor for generating dynamic opening screens. That seemed to still use my CPU which took overnight to complete, even with cuda set for default rendering in blender.

---

### Post by Bucky Ball on 2017-07-02
I have a GTX 970 performing faultlessly with CUDA on Xubuntu-core 16.04 LTS on the recommended driver from Additional Drivers, as advised, so it will, and does, work without issue on Ubuntu 16.04 LTS, too. I bought mine to do HD video post-production and rendering which it does almost silently and running virtually cold (the set up of the box has a bit to do with that, though). Excellent piece of hardware.

This is my second Nvidia card in Ubuntu and they've both worked fine. The first one was ten years ago so that was a little problematic to get going from memory, but all was well in the end. Now, it's a breeze. ;)

As with all questions 'which board to buy', 'which one is best', etc., it comes down to what is best for you. Is CUDA all you need? Then maybe the lowest end GPU that has CUDA. Limited budget? The GTX 970 was the newest when I bought mine and now there is the GTX 1070 (I think that's the number). Do you need it or would the much cheaper 750 be fine? GPUs can get pricey so, like building a computer, best to avoid overkill unless expense is no issue.

(PS: None of your points are issues here. Just install the driver from Additional Drivers, reboot and enjoy your LTS. Yes, LTS is a good way to roll if you need stability. For production machines where you want to avoid downtime. I never use anything else.

The only problem you may have, and I stress *may*, is after you install the card and on first boot. Any issue is generally overcome by booting with the 'nomodeset' option which should get you to a desktop where you can install the driver, reboot and done. We can help you if it comes to that.)

---

### Post by Yellow Pasque on 2017-07-02
> **Bucky Ball said:**
> Just install the driver from Additional Drivers, reboot and enjoy your LTS.

IIRC, Additional Drivers doesn't work for GTX1000 series on 16.04 (because the database is too old). So, you may have to use [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)

---

