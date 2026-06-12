---
title: "RAID Controller and Intel Chipset Support Question"
date: 2024-05-09
forum: Hardware
---

### Post by roby2024 on 2024-05-09
I have a server that a Software Vendor wants me to install Ubuntu Desktop on.

The server is a Supermicro and has an [FONT=&amp]Intel[/FONT][FONT=&amp] C621A chipset and I have a choice between using the motherboard's software Intel RAID controller or an LSI [/FONT]AOC-S3008L-L8E RAID Controller. This server has 4 SATA hard drives in it that will be in a RAID 10 Config.

It's been over 10 years since I've installed Ubuntu, so I was just checking to see if there would be any issues with this chipset with Ubuntu Desktop and which RAID controller would work best with it?

---

### Post by TheFu on 2024-05-10
Never install a Desktop on a server at work.  Fire the vendor for suggesting it.   Ok, I know you can't fire them, but they SHOULD be fired for that suggestion.  Install **openbox** and let them use that. DO NOT INSTALL A FULL DE!

They should be happy with ssh, so give them a hard time for asking for any GUI on a server.  Do they want to waste CPU, RAM, and increase the attack surface 100x for something completely unnecessary?  Having a GUI on a server is doing that.

If there software needs a GUI to run, teach them how to run remote X11 apps from a workstation.  If you need to provide a pseudo-GUI for their server to work, install Xvfb [https://en.wikipedia.org/wiki/Xvfb](https://en.wikipedia.org/wiki/Xvfb) and hound the vendor about their lazy programmers linking to GUI libraries for server code.  Oracle used to do this.  We would embarrass their on-site support people over it every time.  

Don't use the RAID controller built into the motherboard.  Go with the LSI,  With Linux, you may not want to use any RAID controller, since Linux SW-RAID is much more flexible and prevents all sorts of issues that HW-RAID brings.  With Linux SW-RAID, you just need a JBOD controller.  Plus you can use ZFS for the data with extra assurances.  With ZFS, all sorts of capabilities become possible.

So, that's my $0.50.  Don't install a full desktop onto a server. Just don't.

---

### Post by MAFoElffen on 2024-05-11
On the hardware and storage management, I would use the LSI RAID controller as an HBA to pass through the drives as JBOD. That gives you more possibilities, and be flexible & adaptable.

If would recommend using ZFS-ON-Root, which would give you the ability to work on everything, on a live filesystem. Let me explain that a bit. Anything else, you would have the whole system down if the RAID Array goes to degraded, reassembling the RAID array. ZFS goes to degrade, but is still going, while degrade, and lets you Clear a disk, to retry it, to see if the disk is okay to readd... Or replace (remove/add), then resilver. You can do all those things, while still running live.

If your current plan is to have "everything" on one RAID10 storage container, then do 2 mirrored vdevs that have mirrored members. That is comparable to RAID10. What are your reasons for RAID10? There are better faster types out there, where you are not giving up 300% of your storage capacity... Just curious.

If someone chooses a Mirrored solution... I have to ask that question on what there storage policies are, their acceptable risk and loss is... and your availability expectation and guaranty for service uptime. 

ZFS makes supporting those easier and makes future changes possible without affecting your uptime as much as other solutions. I support other solutions. Though... Some things just make sense.

Your plan to put everything into 1 single storage container plan, I would recommend rethinking that. I usually recommend a 3 tiered architecture strategy. In software design, that architecture means that you separate things into an application tier, data tier, and presentation tier. You make things replaceable and adaptable. In IT systems architecture for Server, you provide client services for distributed processing in a 3-tier architecture by separating your OS base, your data, and how it is presented to your clients.

That makes things safer and easier down the road, when you need to upgrade your OS to a newer release, or upgrade the version type of your data, if needed for your data management. Migrations will be much easier. You have to think about the future, for risks, management, and growth beyond day-0.

By using only 1 type RAID10 array, you are putting all your eggs into a single basket. Everything is on a root disk storage container. If something goes wrong in that one piece, you risk everything. See where that goes?

If you add some dividers, who can backup, repair or replace the pieces easier, and more securely.

Example of the basic concepts of that and the tiers (which can be separated further...) of the minimum: OS, userdata, shared data. To do that easier and more effectively might be easier, and more effectively if your added at least 1-2 more minimal sized disks.

Servers are made to be managed remotely. Systems Admins manage servers remotely, whether the servers are in the same room, to the server room/datacenter in the same building or on the other side of the world. The server itself does not need a GUI, and in Linux, that is considered a security risk. Windows Server finally figure that out, and since Win Server 2016, that is why they changed to either having GUI or Core, with core being more secure. Yes, I also support Win Server and VMware vSphere.

A software vendor telling you that you need to install a GUI on a server... I would question them on their reasons. You can install X11 on server and run it remotely from your Linux Management Console remotely.

I do install desktops on some servers, but as minimal, and on demand... meaning, it boots to console, and a minimal desktop can be started temporarily for some types of local management.

You said the Server was SuperMicro. I have some SuperMicro servers here. You can do allot of things through their BMC controller remotely.

Please explain further what you have, what you are trying to do, in a little more detail. Not knowing the details, makes it much harder in recommending a specific tailored solution.

How many servers do you have? Have you thought about a VM Host? Then if they require a GUI for their app, make it accessible to the clients in a VM? For presentation-tier in Server: applications server (remote access to the application on your server) or vm access. Those are ways to provide client server access to applications.

---

### Post by TheFu on 2024-05-11
install X11-Client libraries, not the X11 display server.  If you install just the xterm package, you should get the minimal X11 client-side libraries. We never want anyone stuck sitting inside a data center on a console.  Heck, we don't really want "servers" to even have a GPU at all. Purely console for local access.

---

