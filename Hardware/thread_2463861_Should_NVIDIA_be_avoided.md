---
title: "Should NVIDIA be avoided?"
date: 2021-06-20
forum: Hardware
---

### Post by erosman on 2021-06-20
I am looking to buy a new laptop to install Ubuntu. As a Linux novice, I am hoping for a **hassle-free** migration.

Majority of the laptops in my location, have NVIDIA GeForce GPU and I have read that due to the driver issues, it is better to avoid it and try laptops with AMD GPU.

The most common laptop available to me with AMD GPU is Lenovo ThinkPad but sadly, almost all the available ones are E15 which is reported to have heat issues.

Should NVIDIA be avoided?

*PS. I use laptop for usual computing & programming (with added external monitor), no game-play or intensive video editing.*

---

### Post by QIII on 2021-06-20
The problem with laptops is that the OEMs do not offer Linux users a satisfactory way to use hybrid graphics.  So any laptop with hybrid Intel/whatever graphics is a crapshoot.  Sometimes the BIOS/UEFI allows you to blacklist the Intel graphics and use only the AMD or NVIDIA, but that is not always the case.  When you can do that, however, you will run in to battery use issues as the better GPUs also eat up more power.

The thing about AMD is really only that the APUs combine the CPU and the GPU.  As long as there is not also an Intel GPU, there should be few problems.  Unfortunately, NVIDIA doesn't have CPU/GPU combinations on die.  That is the issue.

My opinion, and you can take it as you wish, is that you are best off purchasing a laptop with an Intel processor and intel graphics with neither AMD nor NVIDIA GPUs.  The next choice would be an AMD/AMD machine with no Intel graphics. It is just less of a hassle.  Unfortunately, NVIDIA is the odd man out here.  That's not the fault of the Linux community.  And it's not that NVIDIA is "to be avoided" just because it's NVIDIA.

---

### Post by erosman on 2021-06-20
Thank you.

> **QIII said:**
> ...you are best off purchasing a laptop with an Intel processor and intel graphics with neither AMD nor NVIDIA GPUs.

Which current laptop series (manufacturer, model) are like that?

> **QIII said:**
> ...The next choice would be an AMD/AMD machine with no Intel graphics.

Which current laptop series (manufacturer, model) are like that?

---

### Post by zircon_34 on 2021-06-20
I have a lenovo with hybrid intel/nvidia graphics, it’s full of problems and unstable for me and am constantly fighting the high dpi 4k vs 1080 external monitor scaling issue. 

Lenovo has a couple of laptops with intel Xe or older intel only. For example carbon x1, thinkbook 13, t480 etc.

I tried one of those intel Xe, it is really like night and day, no hassle, and makes want to boycott nvidia in the future.

---

### Post by Autodave on 2021-06-20
However, on a desk top, I absolutely love nVidia.  I do agree with the others though: especially about trying NOT to get a laptop with 2 video cards in it.

---

### Post by scorp123 on 2021-06-20
> **Autodave said:**
>  especially about trying NOT to get a laptop with 2 video cards in it.

Yup, those suck and 99% of them don't work right under Linux.

---

### Post by monkeybrain20122 on 2021-06-20
Well it depends on the model and the manufacturer. System 76 offers Ubuntu/PopOS laptop with Nvidia GPU, I also have installed Ubuntu on my friend's Alienware laptop without issue. Dell in general has good Linux support. I suggest you figure out what your graphic needs are and do some research on hardware  first, I have had no issue with installing Ubuntu on a few high end laptops with Nvidia.  In terms of performance Intel card is just no match and are pretty useless if you need cuda.

Edited: If I am not sure I'll just install Ubuntu on an external drive first and boot off it to make sure everything works before I wipe Windows so I don't void my warrantee.

---

### Post by scorp123 on 2021-06-20
> **erosman said:**
> I am looking to buy a new laptop to install Ubuntu. As a Linux novice, I am hoping for a **hassle-free** migration.

You could buy laptops with Linux pre-installed, you know? That's about as "hassle-free" as you could get.

Depending on where you live on this planet one or the other choice from this list might be appealing ... or not:

[https://system76.com/laptops]("https://system76.com/laptops")
[https://slimbook.es/en/]("https://slimbook.es/en/")
[https://www.tuxedocomputers.com/en]("https://www.tuxedocomputers.com/en")
[https://puri.sm/products/librem-14/]("https://puri.sm/products/librem-14/")
[https://www.ubuntushop.be/index.php/en/opensource-notebooks/ubuntu-notebooks.html]("https://www.ubuntushop.be/index.php/en/opensource-notebooks/ubuntu-notebooks.html")

My personal take: 

If you're based in the US or Canada I'd give System76 a shot, their machines are suuuper nice and the review videos on YouTube are very positive. For me personally the exchange rate between CHF and USD is in my favor and money isn't an issue ... but my local customs authority loves to snoop on all my packages and slap on hefty import taxes and what not on anything that arrives from overseas to my door step. So for me as European SlimBook in Spain would be a better choice. There are very positive reviews about their hardware on YouTube too.

Even if you decide you don't want to buy from any of the vendors above: Take a look the technical specifications. So all these laptops from System76 and SlimBook etc. are known to work pretty well with Linux ... it should therefore be quite safe to assume that any laptop from a different vendor (e.g. Dell? Lenovo? HP? ...) that is available from shops in your direct area and that has the exact same technical specifications (same CPU, same GPU ...) should thus also work pretty well. Just an idea.

---

### Post by erosman on 2021-06-21
Linux pre-installed laptops are not available in my area.
I have seen few Red Hat Fedora but with low specs.
I intend to get a laptop without OS (no point in paying extra for Windows 10 if I am going to wipe it out).

AFA "*laptop with 2 video cards*" do you mean 2 GPU in addition to the one on the motherboard? Or the one on motherboard plus GPU?

---

### Post by scorp123 on 2021-06-21
> **erosman said:**
>  Linux pre-installed laptops are not available in my area.

Same in my area. But does it matter? Some of the vendors I listed above ship almost world-wide. 

> **erosman said:**
> 
AFA "*laptop with 2 video cards*" do you mean 2 GPU in addition to the one on the motherboard? Or the one on motherboard plus GPU?

Either way... that's 2 x.


> **erosman said:**
> 
Or the one on motherboard plus GPU?

Usually this is how you get 2 x inside a laptop, out of the box. Not counting other tricks like attaching an external one via Thunderbolt port or something like that. Not sure how that would work under Linux.

---

### Post by Yellow Pasque on 2021-06-21
Well, there's no seamless switching "Optimus" support in Linux.
You may be able to use prime-select ondemand like this: [https://ubuntuforums.org/showthread.php?t=2454399&p=14004415#post14004415](https://ubuntuforums.org/showthread.php?t=2454399&p=14004415#post14004415)
But I personally would not buy a laptop with dual GPU's if running Linux. Heck, my nephew got one of those gamer laptops with a powerful Nvidia GPU and he ended up overheating it, and that was probably with Windows.

---

### Post by TheFu on 2021-06-22
I've been extremely happy using the iGPU included in Intel CPUs for years.  No AMD or nVidia GPU at all.  Nothing to fight, since Intel has provided their drivers to the kernel for a very long time.  It "just works" and it helps reduce power requirements that the other GPUs seem to demand. If you aren't gaming, the Intel iGPU is more than good.

IMHO.

I'm not anti-AMD CPU for desktops and servers, but I am for laptops. Intel has nailed the CPU power vs Watt power requirements for many years just perfect.  My intel CPU laptops since around 2012 have all gotten 8-10 hrs of battery life when new. After 4 yrs, most still got over 6 hrs of battery.

---

### Post by erosman on 2021-06-22
I see ..... any suggestions on new laptop ranges without extra GPU?

---

### Post by mastablasta on 2021-06-22
> **erosman said:**
> 
*PS. I use laptop for usual computing & programming (with added external monitor), no game-play or intensive video editing.*

Ryzen 5 or Intel i5 or better.

get AMD/AMD or intel/intel (no additional GPU chip). the latest GPU on chip are more than enough for your needs. just to give you some perspective - my kid has Ryzen 5 3600U with built in GPU and 8 GB ram. he can play many older games (source games like gary's mod, half life 2, CS:GO, L4D2) as well as some less demanding newer ones (Subnautica for example). i saw that even doom 2016 would run at low settings, but he should increase ram to 16 GB and put it in dual channel mode. the new generation (Ryzen 4xxx series) has an even better GPU. situation is quite similar with intel. OK so you won't be having 4K gaming on high frequency monitor with everything set to ultra, but you are not after that right?

for programming a good CPU and plety of RAM is more important i think. 

what to find depends on where you live. Some preloaded linux laptops are awesome.

since you plan second monitor and you might need more disk space you should look into business class laptops. Lenovo, Dell or HP. Avoid those with soldered ram. Get something that is easy to upgrade and repair. business laptops might also be bigger and have better vents & fans.
Dell can come with Ubuntu preloaded. Some HP models are sold with SUSE linux, if you can find which mode that is you can buy one with Suse or with no OS, then you just load the OS. i tiwll work out of the box. I also saw some lower end HP Omens (gaming laptop) with linux preloaded.

if you are going to go with major brands, first check what is available in your area, then notebookcheck website is a good resource to check hardware and see if it fits you needs. when you find a few candidates check in google "installing linux on *chosenmodel*", if it doens't have linux preinstalled. if you don't find anything, then ask here.

for example Dell XPS developers addition was made with developers in mind.

i would go with something that has Ryzen 47xx (or intel i7) and that can upgrade RAM up to 32 Gb with some extra disk space in the box. bur depends what you do exactly and what the budget is. maybe 45xxx or i5 is also enough?

if you go with smaller brands (like system76, Purism, Tuxedo, KDE Slimbook, Ubutnushop, Vikings, Retrofreedom... ) search the internet for linux preloaded laptops. plenty of them.

---

### Post by coffeecat on 2021-06-22
@erosman, I've a somewhat off-topic comment to make, but relevant in the context of this from your OP:

> **erosman said:**
> I am looking to buy a new laptop to install Ubuntu. As a Linux novice, I am hoping for a **hassle-free** migration.

If you make a good choice with regards to graphics, you may still stumble badly with wireless. Some devices are challenging in Linux. If I was in your position and wanted graphics and wireless to "just work" I would choose all Intel - Intel CPU, graphics and wireless. The problem with the tech spec sheets of many manufacturers is that they don't always specify which wireless chipset is used, and if you're unlucky you might end up with one of the difficult ones.

Others have suggested Linux pre-installed laptops. At least you'll know that the wireless and all the other things that need effective drivers will work.

---

### Post by TheFu on 2021-06-22
> **erosman said:**
> I see ..... any suggestions on new laptop ranges without extra GPU?

Most of them do - just avoid "Gaming" in the name.
I agree with the Core i5 or Ryzen 5 or better, but mainly because that is my minimal desire.
However, the RAM and CPU needed depends on the type of programming you are doing.  I've been very happy programming using a $200 Chromebook with a Celeron CPU & 2GB of RAM.  I was writing web server apps in Perl and Ruby.  The machine easily ran a test DB and webserver along with my WSGI webapp and a browser for informal testing.

If I were doing Java or Android development, then the requirements would be much higher. Those both are hogs.

For C/C++, Rust, and any other scripting language development, a $300-$500, laptop would be fine without compromises. I really prefer to program on my Ryzen desktop - more screen area on 2 monitors, faster CPU, more RAM, and a much better keyboard, but my office has lots of workspace for desktop hardware.

My current laptop is this:
```
$ inxi 
CPU~Quad core **Intel Core i5-8250U** (-MT-MCP-) speed/max~800/3400 MHz Kernel~5.4.0-73-generic x86_64 Up~31 days Mem~4679.0/**7847.9MB** HDD~500.1GB(23.2% used) Procs~497 Client~Shell inxi~2.3.56 
```
It is nice for any programming, except Java or Android apps.  For those, I'd want the $2000 Core i9 and 64G of RAM.  For anything else, 4+ cores and 8G of RAM is fine.

I don't keep up with lines of computers that don't have addon GPUs.  Probably any "Business" laptop, but that would be a wide brush stroke. Just stay away from gaming and check.  The marketing won't be quiet about any addon GPU.

I'm ignorant about Ryzen laptop GPUs.  I know that on desktops there was some compatibility problems, at least early on. I just don't know if those have all be addressed. 

One last recommendation - don't by the newest laptop.  Get a model from last year or the year before that.  Avoid the latest and greatest so the Linux driver guys and do their volunteer efforts and so the new drivers have time to work through all the distribution stuff and "just work" when we do a Linux installation.  A 2019 model would be the newest I'd touch, without knowing 100% that the install for a specific version of a specific model "just worked."

Life is too short to fight with hardware compatibility issues.  IMHO, Dell and Lenovo have  the strongest track records on being linux compatible. 

I gotta ask - if you are new to Linux, why buy a new laptop at all?  Can't you just run a virtual machine on your current system and put Linux inside that?  I've been using virtual machines that way, especially for server and my main desktop setup, for over 10 yrs. No need to spend money, unless you just want to spend it.  I ran lots of VMs our 2-core 8GB RAM systems for years.  Plus, virtual machines hide any hardware compatibility issues, since the guest VMs are presented with only the most popular, well-supported, virtual hardware regardless of what is inside the actually physical computer.

---

### Post by erosman on 2021-06-22
> **TheFu said:**
> I gotta ask - if you are new to Linux, why buy a new laptop at all?  Can't you just run a virtual machine on your current system and put Linux inside that?  I've been using virtual machines that way, especially for server and my main desktop setup, for over 10 yrs. 

Currently, I am using an Acer Aspire V3-571G, i5-3230M, 4gb RAM, 750gb HDD (30% used), NVIDIA GeForce710M. Windows 7.
Although it runs fine, the lack of power and RAM has been bothering me. I get the CPU maxed more than I like and that has gradually been bothering me.

Win7 also has become a hassle with lack of support by some software. Some IDE like Android doesn't run properly and updating Windows wont help will the low specs.

Therefore, I have been thinking of getting a more powerful laptop (i7, 10-11th gen CPU, 16gb RAM, 512 SSD). Furthermore, I have been thinking of ditching Windows altogether.

Moving from Windows to Linux would take me a few weeks where I have to set-up Linux, find desired software replacements for my use, transfer my working environment gradually from one laptop to another, without interrupting my daily routine.


Therefore, virtual machine on my current laptop doesn't help me and it would eat up more of the CPU/RAM.

---

### Post by TheFu on 2021-06-22
My main concern is what happens if you have issues loading linux on the hot, new, laptop?  What then?

Moving from Windows to Linux isn't trivial.  It really should be after using Linux for a long time, daily, so your eyes are open and tiny issues don't take weeks or longer to solve.  Plus, Linux isn't Windows and about 80% of the power for it comes from NOT using GUI programs.

Android development needs a $2000 laptop.  16G of RAM isn't nearly enough, IMHO.
A light Linux like xubuntu on the current hardware, then you could run Win10 inside a virtual machine under it.

I'd be very careful with an i7-11xxxx CPU. Those are really new and Linux needs time to develop solutions for new hardware.  

OTOH, I can't blame you for wanting a new laptop.  Have you considered getting a desktop for $450-ish and using a less powerful laptop as a remote connection client back to the desktop?  I've been doing that since 2008.  A $200 chromebook can run an x2go session, securely connect to my workstation back home and let me get work done faster, with less risks, over any network that is ISDN or faster.  Just more options, but I wouldn't blame you for getting a new system either.

---

### Post by SeijiSensei on 2021-06-22
Looks like you can add another 4 GB of memory into your Acer. That's a fairly low-cost upgrade that can often help improve performance considerably.

[https://www.crucial.com/compatible-upgrade-for/acer/aspire-v3-571g-73618g50makk](https://www.crucial.com/compatible-upgrade-for/acer/aspire-v3-571g-73618g50makk)

Replacing the hard drive with an SSD is also a fairly cheap upgrade that can cut down on the time required to boot and do file transactions.

---

### Post by him610 on 2021-06-22
> I am looking to buy a new laptop to install Ubuntu. As a Linux novice, I am hoping for a hassle-free migration.

Why not consider buying one with Ubuntu already installed?  [https://system76.com/laptops]("https://system76.com/laptops")

They make good machines. I have had one for over eight years now - it is my wife's primary computer.

---

### Post by erosman on 2021-06-23
> **TheFu said:**
> My main concern is what happens if you have issues loading linux on the hot, new, laptop?  What then?

Moving from Windows to Linux isn't trivial.  It really should be after using Linux for a long time, daily, so your eyes are open and tiny issues don't take weeks or longer to solve.  Plus, Linux isn't Windows and about 80% of the power for it comes from NOT using GUI programs.

Android development needs a $2000 laptop.  16G of RAM isn't nearly enough, IMHO.
A light Linux like xubuntu on the current hardware, then you could run Win10 inside a virtual machine under it.

I originally started computing on Macintosh Classic II in early 90s and 10 years later moved to Windows (after being ripped off so many times e.g. same software that I paid £385 for Mac was £195 for PC by the same company). 
*I paid £360 for 16mb RAM ...lol... can you believe it!?*

I had dual set-up Mac + PC for about a year and found out that I only work on one and had the added hassle to transfer work if I wanted to work on both (those days with 720kb floppies) and reconnecting monitor and printer. Finally I ditched Mac.

I also tried dual-boot Win/Linux which was not easy those days. I tried Slackware, Gentoo & finally Debian. Even with Dual-boot, I found myself only working in one system (pain to restart every time). Eventually I run into kernel panic and the Linux stopped loading and I was forced to reformat.

Some users need dual-boot to access systems occasionally. I only need ONE computer and ONE system. Laptop suits me as I take it with me when I travel. Desktop is good, in addition to laptop, but as I mentioned, I only want/need one computer.

Thinking of upgrading my laptop for a more powerful one, I was considering the options of staying with Windows (paying $139-$199 for the Win 10 home-pro, $50 for ESET, etc), or ditching and moving to Linux. The dual-boot again doest help with the costs. The OEM Windows might be cheaper, but costs nonetheless.

I thought of using the money towards the cost of the laptop, instead of software.
[I]PS. I only need Android IDE for testing and not development so I would only run it once a while & for a short time.

[/I]> **SeijiSensei said:**
> Looks like you can add another 4 GB of  memory into your Acer. That's a fairly low-cost upgrade that can often  help improve performance considerably.

[https://www.crucial.com/compatible-upgrade-for/acer/aspire-v3-571g-73618g50makk](https://www.crucial.com/compatible-upgrade-for/acer/aspire-v3-571g-73618g50makk)

Replacing the hard drive with an SSD is also a fairly cheap upgrade that  can cut down on the time required to boot and do file  transactions.

I thought about it, but the CPU is still 3rd gen. Then there is the cost of RAM (8gb ~ $40, 16GB ~$70, max 8gb for my laptop though), SSD (512gb ~$100) & Windows 10 (~$139-$199).
Having 8gb RAM might work now but soon it will not be enough.

> **him610 said:**
> Why not consider buying one with Ubuntu already installed?  [https://system76.com/laptops](https://system76.com/laptops)

They make good machines. I have had one for over eight years now - it is my wife's primary computer.

I am not living in UK now and at my location, Linux pre-loaded laptops are not available.

---

### Post by mastablasta on 2021-06-23
in Asia Asus and Dell come linux preloaded. You could get HP or Lenovo with no OS, then load linux after wards..

here are a couple of lists. Some ship worldwide. [https://linuxpreloaded.com/](https://linuxpreloaded.com/)

so unless you are in North Korea, Syria or Iran you should be able to get access to them rather easily.

yes, the biggest issue with upgrade is that when you replace SSD and RAM you are close to price of new one. I have an oldie myself. I was thinking to upgrade the RAM only (and maybe up to 6 GB only from current 2 GB), so it can be used for some web surfing and if they have online school, so we can move them to separate room. if i upgrade to 8Gb and also add SSD the cost would come close to a much better new PC.

---

### Post by linuux on 2021-06-24
> **Yellow Pasque said:**
> Well, there's no seamless switching "Optimus" support in Linux.
You may be able to use prime-select ondemand like this: [https://ubuntuforums.org/showthread.php?t=2454399&p=14004415#post14004415](https://ubuntuforums.org/showthread.php?t=2454399&p=14004415#post14004415)
But I personally would not buy a laptop with dual GPU's if running Linux. Heck, my nephew got one of those gamer laptops with a powerful Nvidia GPU and he ended up overheating it, and that was probably with Windows.
Hello.  As mentioned previously, System76 sells laptops with Linux (PoPOS with nvidia graphics) on it so in theory, couldn't you find a Dell or Lenovo laptop, for e.g.,which has the same mobile graphics chip - and have a laptop running as smoothly as a System76 one?

Just asking.  I don't know much about Laptops with the hybrid graphics - except, last time I paid attention to it, it was Optimus - and developers would probably use 'Windows' - to reverse engineer the drivers, if I'm not mistaken.  You probably have to stick to particular mobile graphics chips - whichever is supported.  

I am just guessing, don't quote me on anything.

---

### Post by Yellow Pasque on 2021-06-24
> **linuux said:**
> System76 sells laptops with Linux (PoPOS with nvidia graphics) on it so in theory, couldn't you find a Dell or Lenovo laptop, for e.g.,which has the same mobile graphics chip - and have a laptop running as smoothly as a System76 one?

In theory, yes, but from someone who looks at these forums and other bug reports, I'd say there are still some rough edges with the PRIME setup, that may require hacking at the command line or changing BIOS settings. I wouldn't recommend it to a non "power user".

I guess PRIME is getting better as Nvidia rolls out driver fixes ( [https://www.nvidia.com/download/driverResults.aspx/176525/en-us](https://www.nvidia.com/download/driverResults.aspx/176525/en-us) ) and distros cleanup their scripts for handling "ondemand" mode. But unless someone's a hardcore gamer or doing serious 3D work, I would advise them to avoid Nvidia or a dual graphics laptop. Don't take that as gospel, because I don't have any hardware in front of me to test out how well prime works.

---

### Post by him610 on 2021-06-25
Will be attempting installation of LTS 20.04.2 on laptop, Acer V3-572G w/i5-5200u and Nvidia Geforce 840m (from ~2015) within the next few days; will post results on this thread. I think I will replace the HDD with SSD first.

Update:
Did not replace HDD. Installed Xubuntu LTS 20.04.2 on the 1TB HDD in its own partition. No issues with the installation. 
Both GFX chips were recognized during the installation.  Drivers for both intel 5500 and NVIDIA GeForce 840M were downloaded. 
 
```

$ inxi -SMCGxz
System:    Kernel: 5.8.0-55-generic x86_64 bits: 64 compiler: N/A Desktop: Xfce 4.14.2 
           Distro: Ubuntu 20.04.2 LTS (Focal Fossa) 
Machine:   Type: Laptop System: Acer product: Aspire V3-572G v: V1.26 serial: <filter> 
           Mobo: Acer model: EA50_HB v: V1.26 serial: <filter> UEFI: Insyde v: 1.26 
           date: 12/18/2014 
CPU:       Topology: Dual Core model: Intel Core i5-5200U bits: 64 type: MT MCP 
           arch: Broadwell rev: 4 L2 cache: 3072 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 17560 
           Speed: 798 MHz min/max: 500/2700 MHz Core speeds (MHz): 1: 798 2: 799 3: 798 
           4: 799 
Graphics:  Device-1: Intel HD Graphics 5500 vendor: Acer Incorporated ALI driver: i915 
           v: kernel bus ID: 00:02.0 
           Device-2: NVIDIA GM108M [GeForce 840M] vendor: Acer Incorporated ALI 
           driver: nvidia v: 460.80 bus ID: 04:00.0 
           Display: x11 server: X.Org 1.20.9 driver: modesetting,nvidia 
           unloaded: fbdev,nouveau,vesa resolution: 1920x1080~60Hz 
           OpenGL: renderer: N/A v: N/A direct render: N/A 

```
Maybe I should figure out how to switch between GFX chips; although, the intel 5500 and i915 driver are perfectly acceptable to me for my uses.

---

### Post by CoopOne on 2021-09-06
I made a successfull installation of MX Linux MX-19.4.1_x64 KDE, AHS (Advanced Hardware Support) on brand new HP Pavilion 15-eg0079nw (FreeDOS preinstalled) equipped with hybrid graphics: Intel TigerLake GT2 [Iris Xe Graphics] & NVIDIA TU117M [GeForce MX450]. MX Linux uses Bumblebee technology for switching GPUs drivers. I couldn`t install Nvidia drivers with Ubuntu on that.

Device configuration: [https://linux-hardware.org/?probe=e76ffa7805](https://linux-hardware.org/?probe=e76ffa7805)

---

### Post by linuux on 2021-09-06
> **CoopOne said:**
> I have made a successfull installation of MX Linux MX-19.4.1_x64 KDE, AHS (Advanced Hardware Support) on brand new HP Pavilion 15-eg0079nw (FreeDOS preinstalled) equipped with hybrid graphics: Intel TigerLake GT2 [Iris Xe Graphics] & NVIDIA TU117M [GeForce MX450]. MX Linux uses Bumblebee technology for switching GPUs drivers. I couldn`t install Ubuntu on that.

Device configuration: [https://linux-hardware.org/?probe=e76ffa7805](https://linux-hardware.org/?probe=e76ffa7805)

I would have tried Ubuntu 21.04.  It should work - both are based off of Debian.  Ubuntu has the Bubblebee package.

[https://www.ubuntuupdates.org/package/core/hirsute/multiverse/base/bumblebee](https://www.ubuntuupdates.org/package/core/hirsute/multiverse/base/bumblebee)

You enabled the third party/non-free repository?   Did it not work - in general - or when everything was configured properly, it still didn't work? 

Just curious.  I cannot test as I don't have a hybrid laptop.  I'm just interested in nvidia and amd graphics situations here - as I plan a build in the near future (hopefully).

Edit: Note, MX Linux uses an older kernel than current versions of Ubuntu 21.04 etc.

---

### Post by CoopOne on 2021-09-06
> **linuux said:**
> 
You enabled the third party/non-free repository?   Did it not work - in general - or when everything was configured properly, it still didn't work? 


I spent almost two weeks and tried dozen modern distributions, different kernels, Secure Boot disabled, using great tool [Ventoy]("https://www.ventoy.net") (OpenSUSE, Fedora, Zorin, Mint, different Ubuntu versions, also 21.04 etc) - nothing worked at all. Always black screen at installation stage, or had to use modeset parameter to boot. I didn`t try third party repository. There were two problems diagnosed: the driver for the newest 11th generation Intel Iris Card cloud not be loaded, and then, I couldn`t install Nvidia driver too (trying different methods: manually, from repository etc).

Reading the official Nvidia forum I made assumption, that it was necessary to have installed Intel driver BEFORE trying to install Nvidia driver. The only distribution, which managed to auto load driver for my Intel Iris version was MX Linux. To be precise - only AHS (Advance Hardware Version). Then, it was easy to install Nvidia driver using special Nvidia installation script provided in MX Linux.

If you want to buy modern notebook and are not so experienced, my recommendation is: use Ventoy on high speed USB drive, disable Secure Boot in BIOS, try different newest distros with different kernels, look for special editions with enhanced support for hardware like MX Linux "AHS" version or OpenSUSE "Tumbleweed". Prove that it is possible to load Intel, and then Nvidia driver on any of that distribution. And then try to diagnose the problem on the distribution of Your choice.

For now, I m using different notebook Dell Precision 5750 hybrid graphics 10th generation Intel i915 + Nvidia RTX 3000, Ubuntu 20.4 with special oem kernel version, which is Certified to work with Ubuntu. Everything works great (except high speed SDXC cards - but I think it will be resolved soon). On that one, the prime-select solution is used to switch between graphics cards.

---

### Post by linuux on 2021-09-06
> **CoopOne said:**
> I spent almost two weeks and tried dozen modern distributions, different kernels, Secure Boot disabled, using great tool [Ventoy]("https://www.ventoy.net") (OpenSUSE, Fedora, Zorin, Mint, different Ubuntu versions, also 21.04 etc) - nothing worked at all. Always black screen at installation stage, or had to use modeset parameter to boot. I didn`t try third party repository. There were two problems diagnosed: the driver for the newest 11th generation Intel Iris Card cloud not be loaded, and then, I couldn`t install Nvidia driver too (trying different methods: manually, from repository etc).

Reading the official Nvidia forum I made assumption, that it was necessary to have installed Intel driver BEFORE trying to install Nvidia driver. The only distribution, which managed to load driver for my Intel Iris version was MX Linux. To be precise - only AHS (Advance Hardware Version). Then, it was easy to install Nvidia driver using special Nvidia installation script provided in MX Linux.

I hope that information will help others, when trying to install Nvidia graphics on modern notebooks. If you are not so experienced, my recommendation is: use Ventoy on high speed USB drive, disable Secure Boot in BIOS, try the newest distros with newest kernels, look for special editions with enhanced support for hardware like MX Linux "AHS" version or OpenSUSE "Tumbleweed". Prove that it is possible to load Intel, and then Nvidia driver on any of that distribution. And then try to diagnose the problem on the distribution of Your choice.

For now, I m using different notebook Dell Precision 5750 hybrid graphics 10th generation Intel i915 + Nvidia RTX 3000, Ubuntu 20.4 with special oem kernel version, which is Certified to work with Ubuntu. Everything works great (except high speed SDXC cards - but I think it will be resolved soon). In that one, the prime-select solution is used to switch between graphics cards.Interesting.   My guess is you have to disable either the Intel or Nvidia at the start.  The problem is overall Linux has done a poor job dealing with this technology.  I noticed that most complaints on various distro forums has to do with hybrid graphics - most recent laptops are nvidia/intel although AMD has some radeon APU graphics laptops but I don't know what the situation is with those - I think they are too new as I don't notice too many posts on it but I wouldn't be surprised if it's also a challenge despite FOSS drivers with AMD.

But, 'Bumblebee' and dealing with hybrid graphics has been an issue for a while from what I can tell - there's also the BIOS and the fact most laptops are Windows-based and Microsoft has license to mess around with the BIOS /Secure boot and all kinds of other stuff.

My advice to people who buy nvidia hybrid laptops is to first look at PopOS and System76 websites because those guys sell nvidia/hybrid laptops and desktops equipped with nvidia hardware - preconfigured.  So, see what steps and instructions they give and apply it to Ubuntu (PopOS is more or less, a highly tweaked version of Ubuntu).  

The problem is there is potential for graphics conflicts and the technology for 'switching' graphics is supported primarily in Windows - Windows OS is the priority so you are looking at smaller groups (Bumblebee etc.) trying to support this.  System76 has a priority to make sure they work out of the box or they'll get a lot of complaints and it will put a strain on customer service - so, at the very least, it should work preconfigured - being able to deal with kernel, nvidia and intel version changes is another story.

P.S.  I'm a big fan of Ventoy.  Great program!

---

### Post by mastablasta on 2021-09-07
> **linuux said:**
> The problem is overall [COLOR=#ff0000]_**Linux has done a poor job dealing with this technolog**_[/COLOR]y.  I noticed that most complaints on various distro forums has to do with hybrid graphics - most recent laptops are nvidia/intel although AMD has some radeon APU graphics laptops but I don't know what the situation is with those - I think they are too new as I don't notice too many posts on it but I wouldn't be surprised if it's also a challenge despite FOSS drivers with AMD.


surely you mean that hardware manufacturers did a poor job in supporting linux here. It's their hardware, their drivers. they chose not to support linux from the start. nvidia just said sorry, we don't support linux. why would this be linux fault? it is amazing to me that nvidia could not support, but a rag tag bunch of people made bumblebee project and behold, somehow, someway optimus can actually work.  and they didn't spend millions of USD to develop it. if nvidia does not have resources and can't see the benefits, i would understand that, but to not give a helping hand to people who can do it for them is ridiculous.


AMD APUs work great. they are not just in laptops but desktop to. with current GPU prices, i am a bit sad i didn't go with APU during upgrade. at least i would have new GPU chip on the APU and it would at least support Vulkan and run some newer light GPU games well.


EDIT: my kid has Ryzen 5 3500U paired with nvme. it works amazingly well for the games he plays. i checked and even this old APU can run Doom 2016 (on low settings) if i increase the ram to 16 GB and make it dual channel. which i might do, but i need to save a little bit of money to exchange the nvme into a bigger one as well. at the moment he is running most games from USB3.0 SSD drive.

---

### Post by linuux on 2021-09-07
> **mastablasta said:**
> surely you mean that hardware manufacturers did a poor job in supporting linux here. It's their hardware, their drivers. they chose not to support linux from the start. nvidia just said sorry, we don't support linux. why would this be linux fault? it is amazing to me that nvidia could not support, but a rag tag bunch of people made bumblebee project and behold, somehow, someway optimus can actually work.  and they didn't spend millions of USD to develop it. if nvidia does not have resources and can't see the benefits, i would understand that, but to not give a helping hand to people who can do it for them is ridiculous.


AMD APUs work great. they are not just in laptops but desktop to. with current GPU prices, i am a bit sad i didn't go with APU during upgrade. at least i would have new GPU chip on the APU and it would at least support Vulkan and run some newer light GPU games well.


EDIT: my kid has Ryzen 5 3500U paired with nvme. it works amazingly well for the games he plays. i checked and even this old APU can run Doom 2016 (on low settings) if i increase the ram to 16 GB and make it dual channel. which i might do, but i need to save a little bit of money to exchange the nvme into a bigger one as well. at the moment he is running most games from USB3.0 SSD drive.
Fair point.   You have everything working with MX Linux, then?

I was wondering if you tried 21.04 with the 'Additional Drivers' software method - after enabling non-free software repository of course - then choose Nvidia version 470.57 or whatever is the most recent there.  

I am not sure how they handle the dual Intel switching - but combined with the Bumblebee software (I linked to in my previous post) - it might work?   (Nvidia lists version 470.63 as the latest driver - as of today - for MX450 so it's clearly supported).

---

### Post by mastablasta on 2021-09-08
i am using Kubuntu (Ubuntu with KDE). they all installed and work well on nvidia (but these are desktops with older ryzens + nvidia card) as well as on systems with APU  AMD (E450 and Ryzen 3500U).

---

### Post by bcschmerker on 2021-09-17
**I've an older system with an nVIDIA® nForce® 780a SLI that I'm prepping for projector duty in a house of worship, and Tesla and earlier is a crapshoot,** nVidia Corporation having dropped support for Tesla at LinUX Kernel 5.4.  340.108 having been declared a WontFix (I had occasional lockups with the stock C77 64-bit *geForce*® GPU in the MCP78 northbridge), I've a long-term project to split the 340 Source consistently with, and backport fixes from, current drivers, but that may take several years.

---

