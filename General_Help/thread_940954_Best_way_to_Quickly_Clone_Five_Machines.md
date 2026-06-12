---
title: "Best way to Quickly Clone Five Machines"
date: 2008-10-07
forum: General Help
---

### Post by ashkev on 2008-10-07
Hello,

I have five machines with the following configuration, they have identical hardware (they are Public Access machines in a public library)

                                AMD Sempron LE-1100 1.9ghz CPU, AM2 motherboard with onboard LAN, Video, and Sound, 512MB DDR2 RAM, 80GB SATA Hard Drive, DVD/CDRW Combo Drive, Keyboard, Mouse, and Speakers. Ubuntu 8.04

My question is, what would be an easy, fast, and cost effective way of cloning these machines.

I have them set up so that they automatically do updates, and I have scripts that restore all of the guest user accounts to a preset state upon reboot.  I set up one machine as I wanted it, then the company that was setting them up and selling them to me cloned the other four.  Now I would like to be able clone them each time I make a change... such as installing a program, so that all five machines will remain the same.  I have used PBA ([personal backup assistant]("http://www.vmware.com/appliances/directory/321")) vmware utility to clone over the network, but it takes a very long time for the process to complete.

I am not opposed to using commercial software, if that is the best option.  Do I need to get an extra drive to use?  Can this be done with a USB hard drive, or would that be too slow?

Thanks

---

### Post by DagMan on 2008-10-07
Are you cloning entire drives, partition tables, mbr and everything?
If it's just keeping files on all the machines the same then rsync is pretty good.

---

### Post by jerome1232 on 2008-10-07
dd is good for imaging partitions, and entire disks. It can't be run on a running system though. Can be used over the network with netcat, or to another disc

partimage I hear is also great, also can transfer over the network or to another disc, offers faster speeds than dd (dd reads areas with no data, partimage skips those), in some cases you may want those area's with no data (like you want to run forensic software on the image)

edit: Correction just like most imaging software partimage works on **[B]*unmounted***[/B] disks meaning no go on a running system.

---

### Post by EmanresuusernamE on 2008-10-07
I recommend Clonezilla, you have to reboot the system you want to clone, and there's a quirk in it right now, but it can do cloning quite nicely, I did 40 Vista machines not too long ago, and the only issue was having to boot from a Vista install disk for a command prompt and repair the MBR of the drive.  And that issue was only cause there where two different types of hard drive in the Vista machines.  Other than that, no problem whatsoever.

The quirk is that whatever disk you copy, say /dev/sdb, would have to be /dev/sdb when you're restoring the image or Clonezilla will think it's corrupt.  This may only be because my disk is bad, or that my version is old, but it will work.

---

### Post by scouser73 on 2008-10-08
I used AptonCD and Remastersys to make two Cd's, the AptonCD disc backing up stuff I had downloaded from the repositories, and Remastersys to make an ISO of my setup. When I'd messed up something, I would install the Remastersys ISO, then install the AptonCD disc, thus making the pc go back to it's original state.

AptonCD: [http://aptoncd.sourceforge.net/]("http://aptoncd.sourceforge.net/")

Remastersys: [http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html]("http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html")

---

### Post by taladan on 2008-10-08
If you need to keep bare-metal images of these machines, you can try PING (partimage is not ghost)

I use it at work to drop and cast images over the network, and it works like a dream.  

[http://windowsdream.com](http://windowsdream.com)

Tal

---

### Post by C.S.Cameron on 2008-10-09
The method in this thread worked for me.
[http://ubuntuforums.org/showthread.php?p=5917188#post5917188](http://ubuntuforums.org/showthread.php?p=5917188#post5917188)
I was using flash drives but hard drives should work the same.

---

