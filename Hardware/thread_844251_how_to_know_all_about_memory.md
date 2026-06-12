---
title: "how to know all about memory"
date: 2008-06-29
forum: Hardware
---

### Post by manfer on 2008-06-29
If I would like to upgrade the memory available on my system, how could I know the type of memory the system needs and the max memory I can install on my system?

Which commands are available from bash to get memory characteristics?

I tried lshw but from there I see the memory is DIMM SDRAM, and I think this is not enough, are not all SDR, DDR, DDR2 and DDR3 memories DIMM SDRAMs? Well, but it also says the memory clock of modules installed is 333Mhz. With that, can I assure the type of memory needed on my system is PC2700 (DDR333)? (I know this is the type of memory installed because I opened the computer and saw it but would like to know to do it for any system with no need to open it)

I have this not clear and that is why I doubt so much, what the type of memory that could be installed on a computer depends on? The bus that connects cpu and memory?

Now the second question, how much memory can be installed? The system has two slots for DDR333. What I tried to guess was which DDR333 modules sizes where available. Looking on www I saw 256Mb, 512Mb, 1Gb modules, and I don't know if there are more sizes. Does that mean I could have 2Gb on that system?

But with lshw other data I see under memory characteristics is:

capacity: 1Gb.

And I don't know if that means max memory that can be installed is 1Gb.

I'm very confuse with all this. Would like to know exactly the dependences of those two questions, memory type on a system and maximum memory that could be installed.

---

### Post by phidia on 2008-06-29
IMO the easiest way to find out what you want is to search the internet/google the make and model computer you want to upgrade.

There are also memory/RAM sellers who offer a chart or interactive webpage to determine the memory plus maximum capacity of your system.

Check out [the site here]("http://www.4allmemory.com/index.cfm?pid=473&kwd=memory%20exact&gclid=CKHE5s3qmZQCFQECGgodcSUI7w") and see how that works for you.

---

### Post by manfer on 2008-06-29
Thanks, That is a good site. I checked it for a DELL Dimension 4550, an I get the same results as I could guess from lshw. The site shows:

- The memory of the system is PC2700 = DDR333 (for 533MHz FSB).
- Maximum memory: 1 GB
- Max size modules are 512Mb ones from DELL shown there.
- Slots: 2 sockets

That should mean the max memory for that system is 1Gb because it has two memory slots and on every one of them can be installed a 512Mb module.

Thanks again for the site. Anyway I would like to know all this in depth (it is not only a question to know the possibilities to upgrade this computer, it is to understand how this issues of the memory on any system works too). Though it could be hardest, any other answers would be appreciate: more bash commands for memory characteristics, and an explanation why being available 1Gb DDR333 modules, they would not be valid for that system if they don't.

Other thing mentioned on that site is:

- Your Dell Dimension 4550 only supports modules made with a specific type of chip. Should you find what seems to be the exact same memory elsewhere for a lower price, it is very possible that the cheaper memory will not work in your system.

What gives me another data. I didn't know that not all memories of the same type (e.g. all PC2700 from any manufacturer) will fit on all systems. If I interpret fine what is said there.

---

### Post by sdennie on 2008-06-29
You should be able to get some of the information you are looking for using dmidecode:

```

sudo dmidecode --type memory

```

That may or may not be useful but, it's the most detailed command I can think of that might answer your question.

---

### Post by manfer on 2008-06-29
Thanks, that command looks very useful to get hardware information.

The only thing I need to resolve now is if there are DDR333 1Gb modules why is not possible to install them on a system that uses DDR333 memory?

Why that 1Gb max capacity on a system using DDR333 with two slots?

What imposes those restrictions on a system?

---

