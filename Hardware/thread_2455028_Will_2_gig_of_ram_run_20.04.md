---
title: "Will 2 gig of ram run 20.04?"
date: 2020-12-11
forum: Hardware
---

### Post by sofasurfer on 2020-12-11
I only have 2 gig of ram right now. Will Ubuntu 20.04 run?

---

### Post by sofasurfer on 2020-12-11
Everything I google say it needs 4 gig. Can you tell me a reason for your alternative info?

PKEASE DELETE THIS POST. Someone answered my first post in this thread and then when I answered his post was gone. I do not see a "delete" button.

---

### Post by guiverc on 2020-12-11
The *tag* mentions Lubuntu, but your question seems to be about Ubuntu, so maybe clarify.

I use a device
- lenovo thinkpad sl510 (c2d-t6570, 2gb ram, i915)

to test Ubuntu &* flavors*, and whilst I'd personally not use Ubuntu on it (I'd opt for a *lighter* flavor), it does run on it.   It'll depend what you want to do, as some web pages in a browser need >2GB of ram, others require minimal ram, so it'll depend what you do with it.

The lenovo sl510 has tested all releases up to and including the current *development* release of *hirsute *(what will be 21.04 on release)

---

### Post by Autodave on 2020-12-11
I would go with Xubuntu.....it will run pretty well on 2G ram.  Ubuntu is gonna laggy.

---

### Post by TheFu on 2020-12-11
Minimal 20.04 without any GUI can run on 512MB. The more stuff we add, the more RAM and CPU are required.
Gnome3 ubuntu, the default desktop, is fairly bloated.  There are lighter options.  All ubuntu flavours can install programs from any other flavour, but that brings in dependencies that may not normally be preinstalled.

Kate uses the Qt libraries.  Gnome stuff uses gtk+, not Qt. Using any gnome program at the same time as any Qt program effectively doubles the required RAM. That's a ballpark, not exact.  Using 1 or 50 gnome programs shares the same gnome/gtk+ libraries. Same for 1 or 50 Qt programs.  That 1st program from each toolkit adds 500M-1G RAM commitment, so each flavor usually preinstalls programs that uses only one toolkit.  If the system has 6+GB of RAM, it usually doesn't matter much, but with 2GB, it matters greatly.

Gnome programs are more popular because more DEs are based on it. Gnome2, Mate, XFCE, Cinnamon, lxde all do.

Qt programs tend to be used by KDE and lxqt DE users.

There are good reasons why distros do things, be we can choose to ignore many of those choices, for a price.

---

### Post by Yellow Pasque on 2020-12-11
I ran a minimal Debian xfce system on 2GB for a while. It's not too bad. The worst part was browsing heavier web pages.

---

### Post by sofasurfer on 2020-12-11
> **guiverc said:**
> The *tag* mentions Lubuntu, but your question seems to be about Ubuntu, so maybe clarify.


Sorry. I am sure I clicked on UBUNTU for the OS tag but obiously I am wrong about that. Yes, I do have UBUNTU.

---

### Post by guiverc on 2020-12-11
You do realize you can boot & **TRY** Ubuntu without installing.

We actually have a *Quality Assurance testcase* for that, and it's how I use some devices for testing, as it allows me to do testing and not lose any data on the existing system (ie. I can run some tests on borrowed equipment if the owner lets me).

[https://ubuntu.com/tutorials/try-ubuntu-before-you-install](https://ubuntu.com/tutorials/try-ubuntu-before-you-install)

I could boot up yesterdays *hirsute* daily on my sl510 (old thinkpad mentioned in prior comment), but you're best doing it yourself.  Trying the OS from thumb-drive (with it running entirely in RAM) isn't the same as an installed system (will be a lot slower; more RAM is used for things normally on disk), but it's still worth a look.

Myself, I'd still opt for a *lighter flavor*.

FYI:  I just booted up Ubuntu *hirsute* daily (not today's, yesterday or day before; *hirsute* is what will be 21.04 on release next year) on the sl510 and it operates...  

On 2GB ram there are many things I'd not want to do; as I already mentioned some web sites are very memory hungry (*they off load the processing of the web page to your local machine; cutting down their server costs*).. but it operates fine.   

Also note, some devices are better than others.  I'd rather use a much older c2d-e8300 desktop (optiplex 755) than a thinkpad i5-m520 (x201) and both have the same 4gb RAM; as the optiplex doesn't share it's RAM with it's GPU, the mobile processor is designed to prolong battery life, even though the i5 is a  later generation & faster.... but I'm somewhat biased too in that I prefer the form factor & great keyboard that exists on my desktops compared to the poor thinkpad (which is still much better than other laptops)

---

### Post by skipbarker on 2020-12-14
I'd use Xubuntu or maybe Kubuntu (it's gotten pretty lean on resource usage lately). Best advice I can give, keep your browser tabs to a minimum.

---

### Post by mastablasta on 2020-12-16
i run Kubuntu 64 bit on 2 GB ram. actually 1.5 Gb ram, because 0.5 GB is reserved for the GPU chip. it runs quite well. it could use more RAM. and i am thinking if i should go ahead and do the upgrade. but i still have Windows 7 starter (supports max 2 Gb ram) on the other side of the disk, just in case i really need to run windows specific app. as we discussed a good solution would be to upgrade my desktop to be able to run Windows in VM there. then i could uprgade this old lappy to 8 GB ram and things will be a lot smoother.

you can have one or two tabs open in firefox. anyway as so as you fill the RAM with applications it starts using disk. that is when things get slow. 
but for playing minecraft, left4 dead, morrowind, World of Padman and some other old games... it is good enough.

---

