---
title: "Hardware upgrade"
date: 2007-12-14
forum: Hardware &amp; Laptops
---

### Post by bsh on 2007-12-14
I have a perfectly working ubuntu machine, used as a server, runs 24/7.
I'd like to completely change the hardware under the hood.
Old setup: noname board, socket A, via kt133 chipset, via ide and memory controller, 3x128mb pc133 sdram, gefroce mx440 agp video, realtek 8139c pci network card.
"New" setup will be: msi motherboard, nvidia nforce2 chipset, nfroce ide and memory controller, 2x512mb ddr-400 ram, same graphics card, onboard nvidia network card. (alternatively, i can use the old pci card too)
I do not really want to reinstall and configure everything.
My question is, is that that simple, that ubuntu will redetect all hardware and load the new necessary drivers and the system will boot? or am i going to encounter problems?
any tips i could do to make the upgrade smooth?

---

### Post by TheLions on 2007-12-14
it should work

---

### Post by utopial on 2007-12-17
sweet
this is wat ive been planning on doing too
pulling my HDD out of my old crappy comp and plugging it into my gf's much better comp as the primary HDD, hoping i dont have to do a thing and ubuntu will autodetect and configure itself for me on start up

---

### Post by bsh on 2007-12-17
yeah it worked nicely
the only problem i have is, the network. the old network card remained eth0 even after the change. it wasn't present but remained eth0, and the new network was eth1
had to edit a few files to make it eth0 again.
other than that, no serious issues

@utopial: this only works when you remain in the same architecture. ie. you can not use your existing linux 386 install on a x64 platform. it is possible it will work, but most likely you'll have some problems.

---

### Post by TheLions on 2007-12-17
> **bsh said:**
> yeah it worked nicely


@utopial: this only works when you remain in the same architecture. ie. you can not use your existing linux 386 install on a x64 platform. it is possible it will work, but most likely you'll have some problems.

x32 shoud work on x64, but x64 won't work on x32!!!

---

### Post by utopial on 2007-12-23
im running ubuntu 7.1 on an amd athlon 64 chip which i think is 32bit:

cat /proc/cpuinfo
processor       : 0
vendor_id       : AuthenticAMD
[B]cpu family      : 6
model           : 4[/B]
model name      : AMD Athlon(tm) Processor
stepping        : 2
cpu MHz         : 1202.746
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 1
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr syscall mmxext 3dnowext 3dnow up
bogomips        : 2408.20
**clflush size    : 32**

the comp ill be switching to is an intel pentium 4 3.00ghz  32bit system (x86 family 15 model 4 stepping 1 genuineIntel ~ 3006 Mhz)

---

### Post by TheLions on 2007-12-23
> **utopial said:**
> im running ubuntu 7.1 on an amd athlon 64 chip which i think is 32bit
.
.
.


you got 64 bit processor and you say that is only 32 bit?=D>

ok check installed version of ubuntu if you got x64 or x32 installed

---

### Post by utopial on 2007-12-23
uname -a
Linux damon-desktop 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

i686 is 32bit i believe. it also says that it is 32 bit in the code i posted above (clflush size : 32)

64-bit will display x86_64

---

### Post by TheLions on 2007-12-23
yea, you have 32-bit ubuntu installed so you can just plug in old drive in new computer.

i recommend before you do that to disable gpu drivers (could cause you a trouble)

---

### Post by utopial on 2007-12-25
ah ok thanks
my current computer was good at the time (very old gigabyte mobo, nvidia graphics card, sb live sound card)
the new computer has some lame mobo with no cards (everything is onboard until/if i decide to get cards) but it supports and has better ram and cpu

since the new comp has onboard vid/snd does it matter and disabling the cards b4 the switch?

---

### Post by TheLions on 2007-12-25
> **utopial said:**
> ah ok thanks
my current computer was good at the time (very old gigabyte mobo, nvidia graphics card, sb live sound card)
the new computer has some lame mobo with no cards (everything is onboard until/if i decide to get cards) but it supports and has better ram and cpu

since the new comp has onboard vid/snd does it matter and disabling the cards b4 the switch?

you should switch your graphic to default (I think is called vesa) cause if onboard has different card (non nVidia)  you wont able to get picture.

Also why you don't put in new one pc a graphic and sound card from old one?

---

### Post by utopial on 2007-12-29
the HDD switch didnt go too well

my hdd was dual boot - xp and ubuntu
wen i chucked it in the new machine, it hangs at 'loading grub 1.5' on booting. i tried fiddling with bios and the best i got was an additional message of 'error 22'

do i need to apply some fix to the master boot record or something? is it cause the xp part of the dual boot isnt recognised by the bios and thus grub fails wen it is trying to bring up the option of a dual boot system? i tried reinstalling grub from the ubuntu live cd but i couldnt get it to boot - i got error 22

btw the new machine used to have a single boot xp hdd

---

### Post by utopial on 2007-12-29
i thought id be a lifer but after using windows again on my new laptop, ive decided to depart with the linux fantasy

ubuntu was ok
u can customise lotsa aspects and it's better than windows in a variety of ways (free, syn pack manager, no viruses/spyware/defrag/etc, faster/efficient) but it lacks in several key features that anything other than a very basic user will require
currently i think it's only at a level that is acceptable by schools and perhaps some companies

key flaws for me:
- Excel: open office calc isnt as good. due to my profession, id consider myself an excel guru. various features arent replicated well by open office and vba code often isnt transferrable from windows to linux. windows excel is not only better but it's wat i use at work, so it's linux's job to be compatible, not the other way around

- Streaming media: lotsa plugins are only made for IE and i tried them on IE4linux and it didnt work. since im a big football fan and require streams to view these matches, this isnt good. i think it also might have stopped me using other streaming music/radio too

- some software just doesnt work, especially the small crappy things u buy such as a language education cd.

- my sound always had problems. 40% of the time it didnt work. but i had a legacy sound card so that's prolly why, despite trying to fix it for 6 months. i doubt this is really an ubuntu issue

- evolution and other email managers dont sync properly with hotmail or wateva mail system u use. they are just email downloaders, unlike outlook which thoroughly syncs (ie if u make a folder in outlook and transfer some emails into it, it replicates the process in hotmail).

im not even a gamer so my demands were pretty low.
in the end there were 3 options:
- dual boot (ubuntu and windows)
- ubuntu with a windows virtual machine running inside when i needed it
- windows

i was gonna take the 2nd option, but the set up effort and maintenance is too high.

so goodbye to linux at least for the moment, good luck and i hope that the next few years brings solutions to these problems. im happy i gave it a shot and have no regrets about it. im grateful for what ive learnt

adeus

---

### Post by jespdj on 2007-12-29
> **utopial said:**
> i686 is 32bit i believe. it also says that it is 32 bit in the code i posted above (clflush size : 32)
No. You see something with the number "32" and then assume that it means that you have a 32-bit processor... The clflush number you see does not have anything to do with whether your processor is 32- or 64-bit.

The Athlon 64 is 64-bit. Why do you think it has the number "64" in the processor name?

---

### Post by utopial on 2007-12-29
i think u'r seeing 64s and assuming that

why does swiftfox make these 2 packages:
[http://getswiftfox.com/deb.htm](http://getswiftfox.com/deb.htm)

Select your processor

    * Athlon 64
    * Athlon 64 (32bit OS)


i686 is categorically 32bit

---

