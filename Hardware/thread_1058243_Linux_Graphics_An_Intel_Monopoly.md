---
title: "Linux Graphics: An Intel Monopoly?"
date: 2009-02-02
forum: Hardware
---

### Post by luvr on 2009-02-02
Until fairly recently, all my computers had an Intel Pentium-family CPU and an nVidia graphics card.

Back in 2003, when I attempted to install Red Hat 9, the graphical installation mode failed. I had to fall back on the character-mode install--no big deal, really. After installation, I couldn't get the X Window System to start--the system would lock up whenever I tried to.

When I searched for a solution, I discovered the nVidia proprietary drivers, which solved my problem: It was the only way for me to run a graphical environment on the computer.

Initially, the nVidia binary blob worked fine.

But, as Linux evolved, the driver apparently couldn't keep up, and gradually deteriorated; this became particularly evident as advanced graphical features were getting implemented--e.g., compiz and the like--and various annoying (albeit not necessarily fatal) bugs began to show up.

Then, in 2007, rumour had it that some people got the impression that AMD/ATI was getting ready to appear to promise that they would *"soon"* release open-source graphics drivers--see, e.g., [here.]("http://itknowledgeexchange.techtarget.com/enterprise-linux/amd-will-deliver-open-graphics-drivers")

I confess: they fooled me too--I believed the rumours. Thus, when I considered it time to upgrade my PCs, I went for AMD-64 systems with integrated ATI graphics.

By now, I realise that the rumours were just that: rumours. There won't be any full-featured open-source graphics drivers from AMD/ATI anytime soon. What's more, their **binary** drivers are absolute rubbish--worse (**much** worse!) than the nVidia drivers ever were.

It could be that the current versions of nVidia's proprietary drivers work fine on current Linux systems (I don't know, since I no longer have any nVidia graphics hardware)--but even so, the fact remains, there's no guarantee whatsoever that they will keep up with future Linux enhancements and improvements; in fact, I'm convinced that they **will** deteriorate again. *(You may disagree, and I'll respect your opinion if you do, but there's no point in trying to convince me.)*

What's more, there won't be open-source graphics drivers from nVidia **ever**--Period. With AMD/ATI, there remains at least *some* hope that they might release (or support) open-source drivers some day--like, next century or so.

That really leaves Linux users who want good, **working** graphics drivers just one choice: **Intel.** In fact, my only computer that runs Linux, including full-featured graphics support, entirely trouble-free (*without* even requiring a binary blob!), is my Dell Studio 17 laptop--which has integrated Intel graphics.

Unfortunately, Intel won't provide any add-on graphics cards--they only support integrated graphics. They won't easily be convinced to develop add-on cards either, especially as Linux becomes more popular: For a satisfying Linux experience, you have no choice but to use Intel graphics anyway, ergo (since you can get Intel graphics only as an *integrated* option) you will have to use an Intel motherboard, including an Intel CPU, as well. Monopoly ensured!

I have no choice but to congratulate Intel for having the guts to take this route--it's a **great** move on their part. My next hardware upgrades will obviously *have* to be all-Intel--**unless** AMD/ATI is smart enough to see the light before they are forced into oblivion.

I'm not optimistic... :(

*(Sorry--I just **had** to get this off my chest...)*

---

### Post by luvr on 2009-04-26
I have just installed (the 32-bit version of) Ubuntu 9.04 (*"the Jaunty Jackalope"*) on an AMD-64 computer that has an integrated **ATI Technologies Inc Radeon HD 3200 Graphics** adapter, and I'm pleasantly surprised at how far ATI graphics support under Linux has come.

The open-source Radeon driver has better performance than it used to have (even though it still won't support 3D acceleration on my hardware), and it positions the display image exactly right on the screen (older versions of the driver displayed the image a little too high).

I have also tried out the proprietary fglrx driver, and even that seems to work fairly well. With compiz display effects enabled, moving the *"glxgears"* window doesn't exactly work right (although the display will get properly restored once the window is at its target position), but with other programs, no such issues seem to occur while their windows are being moved. (It is still possible, though, that some programs that I have not yet tested, will exhibit various problems after all, but that will have to become clear later on.)

I don't consider the proprietary driver a long-term solution, since any update to the kernel or the X Window System or whatnot, may break it, so I went looking for a little more information about the future (if any) of the open-source driver. I found a most interesting article on the [Phoronix]("http://www.phoronix.com") site: [*AMD Pushes Out New R600/700 3D Code*]("http://www.phoronix.com/scan.php?page=article&item=amd_r700_oss_3d&num=1"), which states that *"AMD is finally pushing some workable code into a public code repository."* It certainly looks like 3D acceleration **is** coming to the open-source driver.

I think I'll give it a little more time; I can certainly get by with what ATI currently offers. **If** development really continues in the right direction, then we may (finally!) get to see some real competition on the open-source Linux graphics front!

---

