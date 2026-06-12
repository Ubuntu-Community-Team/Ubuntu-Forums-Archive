---
title: "how to find the right RAM?"
date: 2024-03-17
forum: Hardware
---

### Post by lewisk77 on 2024-03-17
Hello Guys, 

since I'm using ubuntu i am experiencing slow performance issues with my Linux Mint 17 and I believe I need to upgrade my RAM. Can anyone provide guidance on how to find compatible RAM?


During my online research, I came across a configurator that claims to assist in selecting the right RAM [https://www.compuram.de/blog/raminator/](https://www.compuram.de/blog/raminator/). Has anyone here used similar tools before, and can they be trusted to ensure compatibility with the RAM?

Many thanks in advance

---

### Post by him610 on 2024-03-17
I usually go to crucial.com. 
There are other ways though. I just finished upgrading two of my systems.
Determine what you have installed now, and if you have open slots available.
```
inxi -mxxz
```
This is what was returned from the code above...
```

  Device-2: DIMM 1 size: 8 GiB speed: spec: 2400 MT/s actual: 1600 MT/s type: DDR4
    manufacturer: N/A part-no: WPBH26D408SWA-8G

```
Notice it is from a noname manufacturer., but the important information is there.
Search on the part no. "WPBH26D408SWA-8G".  (Use your own part no. here)
The results should show several alternatives.

---

### Post by Autodave on 2024-03-17
Laptop or desktop?  Make and model?

---

### Post by Yellow Pasque on 2024-03-18
```
sudo dmidecode -t memory
```

> Mint 17 

Mint 17 has been EOL and unsupported for 5 years now...

---

### Post by MAFoElffen on 2024-03-18
The OP asked how he could find what memory may be compatible with his system... 

I'm sorry... Most of the given commands I saw are listing what is there. Not what could be possibly be there.

What was useful was asking for more info on the system, as that is what that answer really depends on.

The first place I look is the User Manual and the support Section for the system. They usually have a list of what they know will work. Then I look on the crucial website...

I might not order Crucial branded sticks, but that will give me a part number for the types that work. << Does that make more sense? Then I look up that "type number"... Then shop for deals... When I find a deal, then I go to the Manufacturer, to see if they say if works for what I am trying to find memory for. (The compatibility guaranty...) I don't buy memory unless I have those things.

I have had friends who bought memory blindly, thinking it will work for their system, then find out it doesn't... And got burnt, when for some reason, the Vendor wouldn't take the memory back. Or it works, but not as expected...

I think it was "TheFu"... who ordered matched memory for his own machine. Then some time later, ordered more. Same Vendor. Same brand. Same model & speed. Same part number. ...And his RAM speed dropped drastically.

I've learn by my own experience, and from others, that doing your homework, researching reviews, and getting some feedback from the Vendor on some things, really pay off in the long-run. Some things, it just doesn't pay to skimp on. I still shop around for a good price, but I try to do it smartly.

Some of that, you just can't see far into the future-- That may sound cryptic. I have two systems that use 32GB Sticks. One of the two systems, the BIOS for that specific system now supports 64GB sticks, which doubles that system's capacity. Other's, I had a system that the manual first said it supported a Vendor's memory... Then later, found there were problems and retracted that.  Things do change.

Luckily, I have had pretty good luck selling my old used memory on EBay...

---

