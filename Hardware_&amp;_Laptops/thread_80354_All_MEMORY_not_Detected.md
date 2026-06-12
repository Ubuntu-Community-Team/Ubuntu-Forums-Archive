---
title: "All MEMORY not Detected"
date: 2005-10-22
forum: Hardware &amp; Laptops
---

### Post by LateNighter on 2005-10-22
I'm NEW to Ubuntu but not to Linux as a Whole.

 So I'm a little :???: about SOMETHING?

 I'm using Hoary 5.04.

 I have 2 Gig's of PC3200 DDR Memory Installed but it is only detecting that I have 1 Gig installed?   WHAT GIVES?

 I checked in CMO's it says 2 Gig's, In POST it says 2 Gig's, So I know I haven't Blown a Memory Stick!!!

 Is Hoary only able to detect upto 1 Gig of Memory?

 If so is it still using my full 2 Gig's?

 Every other Linux distro I've ever Messed with has always detected the 2 Gig's that I have installed:rolleyes: 

 So you can Understand my Confusion, "I HOPE".

 Is there a program I can download that will get it to detect my Memory?

 When I first installed Hoary 5.04 it didn't even detect My AMD Sempron 64bit 3300+?
 But after I did the final Install and Setup, it is now.

 I'm running the KDE Desktop Format, but it did the samething Under Genome, so that I know isn't the "PROBLEM"?:mad: 
 Any and all "HELP" is more then WELCOME":KS

---

### Post by aysiu on 2005-10-22
What are you using to detect your memory in Ubuntu?

---

### Post by bored2k on 2005-10-22
the default -386 kernel supports up to 1GB of RAM. Install the 686 or k7 kernel (depends on your system).

---

### Post by RawMustard on 2005-10-22
What about when you have 4 gig of ram and you have the i686-smp kernel with highmem set and Ubuntu still only see's 3 gig :(

Anyone have any ideas how I might get around that problem?

---

### Post by LateNighter on 2005-10-24
[QUOTE=aysiu]What are you using to detect your memory in Ubuntu?[/QUOTE]

:) I went back and checked in synaptic and it said I had the: libc6-I686 package installed.
 Nothing EXTRA just that one.

 Should I go ahead and install the rest of the 686 packages Listed?

 Or should I install just certain ones?

 And if just Certain Ones, Which Ones?

 There was mentioned here about installing the K7 Kernal, is this a possiable fix?

 If so which ones should I Install?

 I am running a AMD Sempron64bit 3300+ Processor.

 Thanks in advance for all your HELP....:KS ;)

---

### Post by codejunkie on 2005-10-24
[quote=LateNighter]:) I went back and checked in synaptic and it said I had the: libc6-I686 package installed.
 Nothing EXTRA just that one.

 Should I go ahead and install the rest of the 686 packages Listed?

 Or should I install just certain ones?

 And if just Certain Ones, Which Ones?

 There was mentioned here about installing the K7 Kernal, is this a possiable fix?

 If so which ones should I Install?

 Thanks in advance for all your HELP....:KS ;)[/quote] what kind of processor do you have amd or intel and is it a 64 bit or 32 bit.
edit: please excuse my ignorance for not fully reading your first post, but now that i see you have a 64bit amd probably the best kernel to use would be the k7-smp, you can do that like this.
```
 sudo apt-get install linux-k7-smp
```

---

### Post by doclivingston on 2005-10-24
Since you are using a AMD system, installing the "linux-k7" package should fix the problem. In case anyone else has this problem, and is using an Intel system, they should install the "linux-686" package.

---

### Post by LateNighter on 2005-10-24
Thanks Codejunkie and Doc i'll give them a try and I'll let ya know how they work.

One thing after I found out the diff between 686 and K7, I loaded some of the K7 and it didn't work so I just clicked install on all the K7 stuff.

It ought to be fun to see what happens???

I figure the most that could happen is I'll end up Reinstalling everything, And being a former XP Pro user I'm use to that. LOLOLOLOLOLOL...

If I install the K7 do I have to uninstall the 386 or is that all Automatic???

---

### Post by codejunkie on 2005-10-24
[quote=LateNighter]Thanks Codejunkie and Doc i'll give them a try and I'll let ya know how they work.

One thing after I found out the diff between 686 and K7, I loaded some of the K7 and it didn't work so I just clicked install on all the K7 stuff.

It ought to be fun to see what happens???

I figure the most that could happen is I'll end up Reinstalling everything, And being a former XP Pro user I'm use to that. LOLOLOLOLOLOL...

If I install the K7 do I have to uninstall the 386 or is that all Automatic???[/quote] no it dosen't uninstall the 386 packages automaticly and not unless you want to but you'll have a bunch of extra choices left in the grub menu.

---

### Post by doclivingston on 2005-10-24
[QUOTE=LateNighter]One thing after I found out the diff between 686 and K7, I loaded some of the K7 and it didn't work so I just clicked install on all the K7 stuff.[/quote]

Both the 686 and k7 packages should work on Intel and AMD systems, it's just that they are optimised for their respective ones. I know a lot of people install the 686 packages on AMD systems.


> If I install the K7 do I have to uninstall the 386 or is that all Automatic???

Installing any new kernel packages does not automatically remove the old packages, so that you can choose to boot into the old kernel if somethine goes wrong.

If you install the new one, and it's working perfectly, then you can remove the old kernel packages.

---

### Post by LateNighter on 2005-10-24
Thanks Codejunkie.

After it finished installing all of the K7 Stuff "Modules" I rebooted checked both New Kernals and seen that they "SHOWED" my 2 Gig's of Memory was Supported.

I thought of uninstalling the 386 but decided I'd let them all stay.

It wasn't going to HURT anything, and I figured what the HEY, it would be a good "SO CALLED" Fail Safe if one didn't Work, I might be able to use the Other One.

Besides I like Choice and thats What Linux is about to Begin With....

Thanks Again...

LateNighter...

---

