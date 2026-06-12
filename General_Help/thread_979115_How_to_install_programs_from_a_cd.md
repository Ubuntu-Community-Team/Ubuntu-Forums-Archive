---
title: "How to install programs from a cd"
date: 2008-11-11
forum: General Help
---

### Post by F4T4LFL4W on 2008-11-11
Well I want to install programs from a cd and i dont see instructions to install. How can I install these programs to my computer?

---

### Post by angryhomer17 on 2008-11-11
Could you be a bit more specific on what you want to install? What is the program name? I'm assuming your trying to install it on Ubuntu. 

If it's a program for windows that you are trying to install on ubuntu, you would have to install wine first. Otherwise, you may be able to find a similar program in Ubuntu. In synaptic you can search by group and keyword and may be able to find an alternative.

---

### Post by F4T4LFL4W on 2008-11-11
i want to install bioknoppix on ubuntu

---

### Post by oilchangeguy on 2008-11-11
> **F4T4LFL4W said:**
> i want to install bioknoppix on ubuntu

ok, you do understand bioknoppix is an operating system that can run by it self right? so if you're wanting to install it inside of ubuntu you'll need to add virtual machine software to ubuntu and install bio there.

---

### Post by F4T4LFL4W on 2008-11-11
Really? I thought it was a bunch of science programs.

---

### Post by oilchangeguy on 2008-11-11
> **F4T4LFL4W said:**
> Really? I thought it was a bunch of science programs.

you might want to try google (which is what i did)

---

### Post by ju2wheels on 2008-11-11
Well Knoppix is different distribution than Ubuntu, so unless you want to erase your Ubuntu setup and install Knoppix, which might be a bit difficult as Knoppix is intended to be run off a Live CD and not really installed.

That said what I think you want to do is rather install the applications that BioKnoppix has on Ubuntu by installing them individually. The bio applications themselves are listed here: [http://bioknoppix.hpcf.upr.edu/applications](http://bioknoppix.hpcf.upr.edu/applications)

You can install them by running the following:
```

sudo apt-get install emboss clustalx ncbi-tools-x11 imagej python-biopython rasmol bioperl

```

This does not include jemboss (which must be compiled from source) or bioconductor.

---

