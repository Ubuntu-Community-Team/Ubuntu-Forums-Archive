---
title: "Need serious help to set up a server"
date: 2008-09-21
forum: General Help
---

### Post by Lucrezia on 2008-09-21
Hello everybody!

I'm a mathematician with understandings both of advanced numerical algebra and parallel programming. Lately there've been a lot of speaking about [CUDA]("http://en.wikipedia.org/wiki/CUDA") and [GPGPU]("http://en.wikipedia.org/wiki/Gpgpu"), and in fact they're a great tool for the scientific community. The problem is that yet have to be made a set of reliable, open libraries to use the power of GPU in the daily scientific (and non) environment. Imagine to use your graphic card to stream a compressed HD video over a poor narrowband connection, or to search terabytes of data for a small record in a second. I think you now understand how this could greatly benefit the whole community: this is why i decided to make this the subject of my thesis, i'll write a (small) portion of the needed libraries, and i'll start an open source project to share the results.


Unfortunately i don't know as much math as IT, therefore i'm here to ask you all for your help: i need to give this idea a concrete aspect on the paper, so i'll be able to show it to my professors and get the approbation. I'll explain you briefly my needs:

In order to program on CUDA i need a portable CUDA capable machine, equipped with the latest Nvidia technology (GTX 260), so i can program on it anywhere i am. Since no such laptop exist, my idea was to set a desktop server equipped with the right hardware, to be used with something like tight vnc. Still there are many details to be taken care of:


1) Hardware

Being a self-funded project, i can't afford to buy a multiprocessor-fancy xeon-machine :D:D:D. Actually i just have an HP nx7400 note, so here's a candidate list of the hardware i'm going to choose, feel free to point any possible incompatibility with linux (Ubuntu):

Intel G43 chipset with Q6600
At least 3 gb of DDR2 ram
Nvidia GTX 260
Raptor 36 gb 10.000 rpm (old, but working!) 
... something else ...

around 800 bucks (no monitor - no keyboard)

1a) Ramdisk

Since i understand from my previous experience with numeric linear algebra that the biggest problem is to keep the CPU (GPU) feeded with data, and since i can't afford yet a SSD, my idea was to buy 8 gb of ram to load the OS with master applications (compiled code, Matlab, ...) to speed up the performance. 
My plan was to have 2 different entries at loading grub: normal ubuntu, and ubuntu loaded on a 6.5 gb XiP (eXecutable in Place) fs, like tempfs.
Very few docs have been wrote on the argument, and almost none mention the performance improvements. Do you think that this could actually give a noticeable increment on my performance? Any idea on how to do so?

3) Reliability and responsiveness

I'm afraid that i'll buy the machine, just to find out that the system is too slow to respond because tightVNC doesn't work very well.

Do you think that remote computing is reliable? How much difference there will be from remote computing, and using the machine from local?

The server would be behind a fiber optical 10 mb/s connection, with a private ip (see below).

4) Reachability

Unfortunately my isp doesn't give me a public IP and i can't acess the router (an HAG; Home access gateway) to open a port. So my server is behind a nat and i have to reach it without an external server.

From my scarce knowledge of TCP/IP I understand that this is possible, still a bit difficult. An easy solution would be to use Hamachi, but it's closed source, and i dislike closed solutions. I could use openVPN, but i need your help to understand how openVPN could help me.




I apologize for being too much loquacious, and for my terrible english , but it's not my first neither my second language :P Thank you all for the polite answers in advance; i hope that our efforts will make the open community a better place!

---

### Post by cszikszoy on 2008-09-21
You might find a lot of useful information here:

[http://fastra.ua.ac.be/en/index.html](http://fastra.ua.ac.be/en/index.html)

It's a computer built for number crunching at the Uni of Antwerp using 8 GPUs and cuda.

Some interesting things that they point out are that they use a slow harderive (compared to the 10k rpm or SSDs that you talk about) because HD access is not the bottleneck with these computations.  Also, they use a slower CPU (I think that tri core phenom is a bit slower than the one you mention) because again, the CPU is not the bottleneck.

With CUDA you aren't doing much work on the actual CPU, most everything is done on the GPU.

---

