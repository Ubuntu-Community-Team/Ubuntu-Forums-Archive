---
title: "Create an updated reinstall CD/USB Image"
date: 2009-11-05
forum: Installation &amp; Upgrades
---

### Post by KingLear0 on 2009-11-05
I have a sort of random question to see if anyone has a solution or answer for.  

I like to play with my systems, try new versions, software etc.  As  a result, I tend to reinstall my OS fairly often.  to save my data, I keep my /home on its own partition.  My question relates to the reinstall of the main / partition.  

Like everyone, I get my system to a state that I like it, all my programs are setup and installed, everything on my laptop/desktop is working correctly.  But I lose all that careful setup work if I choose to try a different flavor of linux or if an upgrade goes horribly, horribly wrong.

In Ubuntu, (I'm on Karmic at this time), we install all the updates and software up to some date.  Ubuntu has downloaded all the install files, scripts and debs required to install these updates and software and they are kept around in the /usr/src directory if I remember correctly.

So on to the actual question:  Is it possible to create a new install image (CD or USB image) that will automatically install the updates without having to re-download them, if I choose to install over my current setup?  

My thought process would be that I could make a clone of the partition, then find a way to write the cloned partition back onto the / partition when I wanted to restore a working system.  My issue with using a straight clone is that, from my understanding, you need an equal amount of space to store the clone on, and I don't have a DVD or USB drive that will hold my 25GB / partition (albeit, the 25GB is only about 4 GB of actual data).  

So does anyone have any experience 1) making a clone of a large partition and shrinking it to fit in a smaller storage unit, and 2) using that clone, via a live CD I assume, to recreate an installed system.

The end goal of this is to be able to tweak my Ubuntu installation to exactly how I like it, then be able to install say, Fedora or Mac osX, to try some new software, and afterwards have my Ubuntu installation back without having to re-download all the updates.  And no, setting up extra partitions to do the testing of other system is not an option at this time due to hard drive space constraints.

I think at this point I'm just rambling, so if I haven't explained myself clearly (which is very, very possible) please ask and I will attempt to clarify.

---

