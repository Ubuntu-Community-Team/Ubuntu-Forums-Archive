---
title: "software virtualization like Altiris SVS?"
date: 2008-07-12
forum: General Help
---

### Post by helwitch on 2008-07-12
I'm looking for a software (rather than operating system) virtualization service, similar to altiris for windows. I have a program I can't get working under wine (MS Money 2008) and I thought perhaps if I created a virtualization package for it under windows, I could then get the virtualization working under linux. Alternately, if anyone knows how to get money 2008 working under wine, that'd be awesome.

---

### Post by jamesdcarroll on 2008-07-12
I've never seen Altiris, but [[COLOR="Blue"]VirtualBox[/COLOR] ]("http://www.virtualbox.org") is open, free, and breeze to use.  I have a Win2K vbox just so I can keep MSMoney around. 

Have fun!

---

### Post by helwitch on 2008-07-12
What kind of system resources does that use? I know under windows, just virtualizing one program was a lot more resource friendly than virtualizing an entire OS. I've got 4Gb of RAM and a 2.2Ghz 64 bit processor, tho I'm running 32 bit Kubuntu cos 64 bit is just too much hassle.

---

### Post by p_quarles on 2008-07-12
First off, I'll say that I'm not familiar with Altiris, so am not really sure what category of application it is.

In any case, there is no such thing as "virtualization" that doesn't virtualize the OS. Virtualization refers to creating a software computer -- this computer functions just like a physical computer, so without an operating system it won't be doing much. 

High-performance usage of a non-native application would be done one of two ways: either through optimized virtualization or through emulation. The former would involve stripping the virtualized OS down to the minimal functionality required to run the specific needed application. Emulation is essentially what Wine (despite their claims otherwise) does: it creates a Windows-compatible API that runs in Linux. 

Both of these solutions are difficult when you are attempting to use an application that is both A) closed source, and B) running on a closed platform. 

So, the honest answer to your question is that Money 2008 is going to be difficult to run in Linux due the fact that it's new -- this means that it will not only be resource-heavy in a VM, but much less likely to work with Wine of Crossover Office.

---

### Post by helwitch on 2008-07-12
> **p_quarles said:**
> First off, I'll say that I'm not familiar with Altiris, so am not really sure what category of application it is.

In any case, there is no such thing as "virtualization" that doesn't virtualize the OS.
Saying 'I've never heard of this software, but I'm quite sure that what it is doesn't exist' sounds pretty silly. I suppose you could quibble that running software in an isolated package with all the dependencies it needs included isn't TRUE virtualization, especially if your definition of virtualization is virtualizing an OS. It's close enough to be called virtualization IMO, and clearly in the software creator's opinion as well. Thanks for trying to help just the same. I'm gonna give this thread a bit more time in hopes someone else will pop up to say 'oh, yeah, I did that, it worked great!', then just go ahead and bit the bullet, boot windows, make the money 2008 package and see how well it runs under wine.

[http://en.wikipedia.org/wiki/Application_virtualization](http://en.wikipedia.org/wiki/Application_virtualization)
[http://www.symantec.com/business/products/overview.jsp?pcid=pcat_infrastruct_op&pvid=sv_sol_pro_1](http://www.symantec.com/business/products/overview.jsp?pcid=pcat_infrastruct_op&pvid=sv_sol_pro_1)

---

### Post by p_quarles on 2008-07-12
> **helwitch said:**
> I suppose you could quibble that running software in an isolated package with all the dependencies it needs included isn't TRUE virtualization, especially if your definition of virtualization is virtualizing an OS.
I'm saying that it sounds like an emulator, not that it doesn't exist. In other words, the equivalent is Wine, which has its limitations due to Windows' closed API. 

Virtualization (with respect to computers) refers to virtualizing a computer. Again, you can no more operate a virtual machine without an operating system than you could operate a physical computer without an operating system. This fact, of course, doesn't prevent software vendors from saying that something is "virtualization" when it isn't, and that's what I suspect. 

> It's close enough to be called virtualization IMO, and clearly in the software creator's opinion as well. Thanks for trying to help just the same.
Whatever you or I want to call it, the point is that the closest you are going to get to that kind of functionality in Linux is with Wine or Crossover Office. Running Windows applications is a popular subject on this forum, and I can assure you that all the options for doing this have already been listed in this thread.

---

### Post by helwitch on 2008-07-12
> **p_quarles said:**
> Running Windows applications is a popular subject on this forum, and I can assure you that all the options for doing this have already been listed in this thread.
If you say so, certainly you must be right.

---

### Post by lovinglinux on 2008-08-29
I'm very familiar with Altiris SVS, which I consider a great Windows application.

Despite the fact that what Altiris do is indeed "software virtualization", I don't think it has any compatibility or emulation capabilities. Altiris simply captures all file and registry operations during install and put them on virtual layer. Every time you run the application, Altiris temporarily add those modifications to system, fooling Windows to believe that the software is actually installed. Any file or registry operations conducted while running the virtualized software are kept inside the virtual layer and are deleted if you remove the layer. Once the layer is removed, no traces of the virtualized software is left behind. So basically, Altiris is a Sandbox that can prevent dll incompatibilities, prevent malware infections and also provide the ability to run different versions of the same application on a single machine.

Altiris can also be used for software distribution. Since it also has two kinds of layers (writable and not), all file and registry operations conducted after the creation of virtual package are kept in a special writable layer. If something goes wrong you can delete the writable layer and restore the original state of the package. like a virtualbox snapshot. But you can also modify the other layer. For example I had a game application layer in which I installed the software core, applied patches, modified the configuration files and exported it to a SVS package. With this modified package I could format my system drive, install Windows, install Altiris SVS and import the package as layer, so I could use the game application within minutes after installing Altiris, with all patches and configuration files included.

Now talking about Linux....

What you want is a "software virtualization" application capable of running Windows applications under Linux, but unfortunately this is what Wine does. So I guess you can consider Wine a "software virtualization" tool with compatibility/emulation capabilities provided by the Windows API. I'm not sure if Wine can contain all file and registry operations inside it's layer like Altiris do, but it certainly virtualizes Windows registry, services, drive mapping and installation folders. Additionally, it can also virtualize libraries on a per application basis using the configuration GUI.

I think your idea is interesting. For instance, when I install America's Army game with Wine, it also install the PunkBuster services. Since Wine virtualize everything in the same layer, every time I run a Windows application under Wine it loads the stupid PunkBuster services, making Ubuntu lag like hell. If a per application layer is implemented, all applications running under the emulation layer could be loaded with their exclusive dependencies. This way I wouldn't have PunkBuster being loaded by Wine every time I run any Windows application. Obviously that this approach could create other problems, specially if you try to run two virtualized applications at the same time, Well I'm not a programmer, so I don't know if it would be possible to load only those dependencies that are not loaded yet.

Anyways, I have found this thread because I was thinking about making an experiment and run Altiris under Wine. If this works, I could run the game I want inside an Altiris layer, inside Wine. So, if I do not activate the game layer I can avoid loading the PunkBuster services with other Wine applications. To test this I will setup a virtualbox, with Altiris under Wine. I will post my results soon.

---

### Post by helwitch on 2008-08-29
It had been my thought as well, that installing in Altiris and then running the Altiris layer in Wine would be a great way to get otherwise wine incompatible software working in linux. However, the software I was most interested in, MS Money 2008, wouldn't even install to an Altiris layer. I am quite curious to hear how your experiement turns out tho, please do update!

---

### Post by lovinglinux on 2008-08-29
> **helwitch said:**
> I am quite curious to hear how your experiement turns out tho, please do update!

Unfortunately, I couldn't install Wine inside the Virtualbox. I get an incompatibility message related to i386 architecture. It seems that the virtualbox creates incompatible virtual hardware.

I'm not sure if I will do this experiment on my host machine.

---

