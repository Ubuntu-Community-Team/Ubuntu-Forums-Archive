---
title: "Ubuntu Live bootup issues"
date: 2008-06-08
forum: Hardware
---

### Post by sarne on 2008-06-08
[SIZE="3"]**Some background: **[/SIZE]
[LIST]
[*]I remotely support a few hundred Ubuntu Live DVD users
[*]I am not a Linux programmer in any way (our company has one though)
[*]I've never had to post in these forums for help before,  I've always found resolutions to hardware compatibility issues just by searching Google
[*]All users are sent 2 DVDs, in case 1 gets scratched or had a bad burn.
[/LIST]

Normally we would go to our programmer for something like this, only the user needs to be up and running by tomorrow if possible and our programmer is unavailable for a while.

Our Ubuntu DVD has 2 Kernel options, Gutsy Gibbon & Hardy Heron.  As well as our programmer has added an F2 Kernal Options menu which allows us to select between some commands(?) to attempt to correct hardware conflicts (that is how I have been able to avoid posting, I would search Google for the issue and normally I would find a Kernel Option which could be used, like *noapic*)

Sorry for the long-winded intro, I didn't want to miss anything

[SIZE="3"]**Issue:**[/SIZE]

*Boot with Hardy Heron *& get a nice vague BusyBox error.  Nothing to go with it.

*Boot with Gutsy Gibbon *& the boot just freezes at a point where I think it's trying to access one of the config files.  The user I was helping was so lost I did not ask for any specifics as she just kept rambling on a lot :confused:

**[SIZE="3"]HARDWARE:[/SIZE]** I pasted any specs I thought might be useful.
(Packard Bell iMedia 1309)
[http://support.packardbell.com/uk/item/?pn=PB34244901&g=1400](http://support.packardbell.com/uk/item/?pn=PB34244901&g=1400)

Bali (GA-K8VM800MNF) µATX Motherboard Ver 1.01
Name: Bali (GA-K8VM800MNF) Ver 1.01
Manufacturer: GIGABYTE

AMD Sempron 3100+

Philips DVD+R9 drive
Product Name:DVD8701

Seasgate Alpine Block Point / Barracuda 7200.7
Density: 80 GB/platter

**We also have the users run a hardware discovery program in Windows, this is a little info from it:**
Video: VIA/S3G UniChrome Pro IGP
RAM: 2gb
System Model: Packard Bell NEC Packard Bell Computer PB34244901
Motherboard: NEC COMPUTERS INTERNATIONAL K8M800-8237 
NIC: Realtek RTL8139/810x Family Fast Ethernet NIC

*She's using a Wireless Keyboard & Mouse.*


Thanks for any input or help you can give.


EDIT: It seems like it has something to do with the video card.  Our programmer is going to see what he can do.

---

