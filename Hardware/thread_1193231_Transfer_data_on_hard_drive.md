---
title: "Transfer data on hard drive"
date: 2009-06-21
forum: Hardware
---

### Post by theozzlives on 2009-06-21
I have a Dell Inspiron 1525 w/160 GB HD. I just bought via ebay a 320 GB HD. I'd like to do a direct transfer of data from the old one to the new one. I have a SAMBA network and a desktop that can handle my data. I can't install 2 hard drives on my laptop and it's the only SATA machine I own. I'm skeptical about creating a tarball, but that's the only solution I can see. Any suggestions?

---

### Post by tgalati4 on 2009-06-21
Put new drive in usb enclosure.
plug in.
sudo fdisk -l
write down disk assignments (/dev/sda for boot drive, /dev/sde for external, for example)
sudo cp /dev/sda /dev/sde  (This will take a while. 10-20 min.)
swap drives
boot
use gparted to capture remaining space.

---

### Post by x22 on 2009-06-21
if you had a USB to SATA converter cable such as eBay
220421416650 you could use the free "HDClone" utility--
it's a nice frontend to the digital dumper "dd"

1. put new drive in laptop
2. connect old drive externally
3. run HDClone frm the CD drive

---

### Post by theozzlives on 2009-06-21
> **tgalati4 said:**
> Put new drive in usb enclosure.
plug in.
sudo fdisk -l
write down disk assignments (/dev/sda for boot drive, /dev/sde for external, for example)
sudo cp /dev/sda /dev/sde  (This will take a while. 10-20 min.)
swap drives
boot
use gparted to capture remaining space.

I was hoping to find a way without extra expence. Besides, an enclosure I'm only gonna use once?

---

### Post by theozzlives on 2009-06-21
> **x22 said:**
> if you had a USB to SATA converter cable such as eBay
220421416650 you could use the free "HDClone" utility--
it's a nice frontend to the digital dumper "dd"

1. put new drive in laptop
2. connect old drive externally
3. run HDClone frm the CD drive

Can I use HDClone or dd across the network if I mount a share to a folder?

---

### Post by arjay27529 on 2009-06-21
this is not a reply to the question in the title, but i cannot figure out how to start a new thread to ask my questions:

1,  i have ubuntu 8.04 installed.  it was working as expected - for several months.  i was out for a week with the pc turned off and when i returned the following occured:

a.  when booting from the hard disk (a routine boot) ubuntu boots as expected until it reaches the logon screen then it either:

crashes immediately or crashes as i start to input the logon - and the pc emits a high pitched tone.  

touching the on/off button causes the tone to discontinue and the machine resets - when back on ubuntu finishes the routine logoff procedure - and when completed it turns off as in a routine shutdown.

b.  when - as now - i boot from the 606 (?) cd everything works as expected.  can do all work routinely -

that is until i leave the machine unattended so that it (apparently - havent watched this fully) enters sleep mode.  then the crash and high pitched tone happens (just as above).  though usually the on/off button is not operational.  need to unplug the pc.

if i shut down normally - when booted from the cd - it shuts off as expected without any problem.  

when booting from the cd - the two internal harddrives are displayed in file browser but are not available - receive this message:

error: device /dev/hda1 is not removable

error: could not execute pmount

the floppy, cdrom, dvd burner and 2 usb drives are all available.

2.  before leaving i copied the entire contents of the "c"/boot hard disk to a usb drive.  questions here:

a.  when i copied, did i get all the necessary files - or are there hidden files that didnt copy? i routinely expose all files in file browser and they would have been listed during the copy.

b.  if i got them all can i simply copy them to a new harddisk from the usb  and it will then be a bootable harddisk?  or do i have to do something special - like formatting or creating a boot sector (as is done in windows).  if this is the ultimate solution, should i install ubuntu 6 and  copy the files from the usb over it - or would ubuntu get seriously confused if i did that?

3.  how do i (can i) mount the internal drives so that i can access them while booted from the cd?

4.  newbie question - exactly where & how do i start a new thread (where i know these questions should be listed)

i know that the problem may or may not be a ubuntu problem, but it doesnt seem to me that it is a mother board / memory / processor problem - else i wouldnt be writing this right now.  it might be a power supply problem, but if so why the apparent software/opderating system issues?  

tho fairly new to ubuntu/linux ive been futzing with pcs for 25 years (since cpm) and have NEVER seen anything like this.  the tone is what really puzzles me:  is it the power supply - why does it work so long as i am actively using the comptuer and then crash only at the logon on screen or in sleep mode.  is it the harddisk - ive heard them make noise but never emit a steady tone.  is it the memory/processor/mother board?  again why is it failing in those two circumstances.  is it ubuntu - if so why/how the tone.  in a word - weird!!

by the way the pc is a dell with a 1.4 mhz p3 or 4 (not sure which) processor and 768mb ram.  so any and all help anyone can offer will be MOST GREATLY appreciated.

---

### Post by theozzlives on 2009-06-21
you click "New Thread"... you don't just hijack a Thread with a totally irrelevant question

---

### Post by tgalati4 on 2009-06-22
One question per post.  I'm browsing with an n800 which has no keyboard, only a stylus hunt-and-peck.  Brevity is good.

1.4 GHz  PIII is probably 8 years old.  Power supply capacitors go bad and whistle.

Yes there are hidden files. They may or may not be copied depending on what you did.

Start a new thread and take one step at a time.

---

### Post by arjay27529 on 2009-06-22
thank you for your responses and assitance especially regarding protocol.

one more question - just where exactly is NEW THREAD - i have looked but cant find it (which i would have used had i been able to find it).

---

