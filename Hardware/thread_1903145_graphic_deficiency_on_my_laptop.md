---
title: "graphic deficiency on my laptop?"
date: 2012-01-01
forum: Hardware
---

### Post by Silas1989 on 2012-01-01
Hello everyone,

I seem to have run into a problem with ubuntu on my laptop, as it seems to be incapable of running (some) games on a normal way.

I first noticed a problem when i installed age of empires on this pc.. once i finally got it working through Wine, every change of frame made the screen flash with weird colors and the game was unplayably slow, even after having tried various tricks like the ones offered on winehq. By then i though that wine could be the problem..

However, once i gotten to install Nexuiz (a fps), which is by the way installable on ubuntu, so no wine this time, but this game has an incredibly slow framerate, even on the lowest settings possible.

Now this laptop isn't one of the faster ones, but it still was capable of doing more than it is showing now, so i'm guessing ubuntu has trouble using the graphics card in this pc, as i am also unable to find the drivers that make this kitten pur. 

do note that games like xmoto or warzone 2100 are playing smoothly, im guessing they put less of a strain to the pc, so that perhaps the cpu is strong enough to carry the burden?? 

some technical info:
the laptop is a toshiba sattelite A200-1k8
2 GiB physical memory
Genuine intel CPU T2130 @ 1,86 GHz x 2
intel 945GM x86/MMX/SSE2 (graphics card)
32 bit OS (ubuntu 11.10)

and i most frequently use the Gnome3 shell, but changing back hasn't solved the problem.

I hope you guys (or galls) can help, Thanks in advance :)

---

### Post by 73ckn797 on 2012-01-01
I have A Toshiba laptop with very similar specs. There are no graphics drivers that I can find either but for my needs I do not need more graphics power.

Check out Playonlinux in the repositories and on the web [http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

Virtual Box, also in the repositories allows a full Windows install inside Ubuntu. Not sure of the performance of games but you can install and run Windows programs just as if you have a separate Windows OS. [https://www.virtualbox.org/](https://www.virtualbox.org/)

Hope this helps.

---

### Post by Silas1989 on 2012-01-02
Thanks, i'll check those out :), still a shame of nexuiz, but bad luck i gues..

---

### Post by gradinaruvasile on 2012-01-02
1. Intel cards have bad drivers under Linux (slow and not stable when opengl comes into play). The drivers used in Windows are far better.
Native games that are more complex than ioquake dont work well with intel under Linux. And forget about Wine because the Windows games usually use many video (directx usually) functions that are untranslatable to opengl because the Intel driver does not support them in the first place.
In contrast AMD/Nvidia's proprietary drivers have almost the same level of support on Linux and Windows (except on Linux only Opengl is supported).
2. VirtualBox uses the systems video capabilities and is limited by both the native Linux driver and the virtualization methods. There is opengl function pass through that makes the virtualized card work almost as fast as the native one, but you will NEVER get faster video in VirtualBox especially if the native drivers are slow AND the driver has limited opengl funtions (which is the case of Intel drivers).

Shorter answer: Dont use Intel video cards if you want to play anything that has shiny graphics. Unfortunately on laptops you are kinda screwed. If you plan to buy a laptop, use either AMDs APUs or dedicated AMD/Nvidia cards (same goes for desktops though, only that with laptops integrated graphics are more recommended because they dont tend to burn out).

---

### Post by Silas1989 on 2012-01-02
so essentially im f*cked??

---

### Post by Mark Phelps on 2012-01-02
> **Silas1989 said:**
> so essentially im f*cked??

IF by that question, you mean that you can't run Windows games in a different OS, when the drivers and hardware aren't available to do that ... then the answer is YES.

---

### Post by Silas1989 on 2012-01-02
wonderfull :D 

yet i also meant that i can't play nexuiz or any linux-game that requires more than meager effort of my graphics card!!! 

Is this also the case??

---

