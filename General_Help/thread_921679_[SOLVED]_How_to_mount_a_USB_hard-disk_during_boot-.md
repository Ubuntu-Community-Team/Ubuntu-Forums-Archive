---
title: "[SOLVED] How to mount a USB hard-disk during boot-up?"
date: 2008-09-16
forum: General Help
---

### Post by blueturtl on 2008-09-16
So I have an external USB hard-disk that I formatted as EXT3.
Now I want to mount it every time the system starts so I add the following entry to my fstab:

```
#external Seagate FreeAgent HDD
/dev/sda1 /mnt/freeagent ext3 defaults 0 0
```

Problem is at boot I get the following error:
Mount: special device /dev/sda1 does not exist!

After I log in and run '(sudo) mount -a', it works just fine.

My guess is that the module that loads the USB storage support and creates /dev/sda1 has not yet been loaded when fstab is being run. What is the best way to get this hard-disk mounted automatically?

---

### Post by blueturtl on 2008-09-17
Bump. Anyone?

---

### Post by Bucky Ball on 2008-09-17
Not sure why you would want to do this but ... You should be able to just switch the drive on and it will automount after a few seconds and provide an icon on the desktop, but if you want to, this is how you would mount an internal drive and see if it works. You need to create a mount point.

cd to /media then:

**mkdir /media/nameforyourdrive** (the name of your drive - ie /media/external)

then, you almost had it right.

Open your fstab file (sudo nano /etc/fstab) and type:

```
# /dev/**sd??**
UUID=**4317640b-79fe-4ee4-a761-84f84991256e** /media/**nameofyourdrive**  ext3    relatime,errors=remount-ro 0       1
```Make sure it is two lines, exactly like this. You can use what is already in the /fstab as reference. You need to change the parts I have in bold. You need to get the correct uuid by typing:

**sudo blkid**

I really doubt that your external drive will be sda. It will probably be last on the list - sdb if you have 2 hard drives, sdc if you have three, etc. Make sure you have the correct sd??. This is very important. If you can't tell from 'sudo blkid', then try:

**sudo fdisk -l**

Learn more:

[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

[http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu](http://users.bigpond.net.au/hermanzone/p10.htm#Mount_a_different_Linux_filesystem_operating_system_in_Ubuntu)

Could you provide a little more detail next time you post ie: What version of Ubuntu you are using. Let us know how you go. :)

---

### Post by blueturtl on 2008-09-18
Thank you for your advice!

I have success as far as getting the drive to automount, but we're not quite out of the clear yet:

Originally I got an error regarding your parameter 'relatime' and hard-disk wouldn't mount:
Mount: unknown option relatime

I then improvised and entered 'defaults' in it's place in fstab and now the drive mounts, however I get a different error during startup:

fsck.ext3: unable to resolve UUID (my UUID)
fsck died with exit status 8

Then I have to press Ctrl+D to resume booting.

This current system is actually not a flavor of Ubuntu, but Debian Etch 4.0. :oops: I have it running on PC that is too old to run a fully fledged Ubuntu. I figured going with Debian would be a smart move since Ubuntu and Debian share many fundamental features. Why automount an external USB HDD? To share this large hard-disk on the home network. It has to be external for a lot of reasons which I won't go into here.

p.s. For whatever reason all my internal devices are as follows:

/hdax - primary hdd
/hdbx - linux hdd
/hdc - cd writer
/hddx - additional hdd
/sda1 - external Seagate FreeAgent USB HDD

My current fstab entry looks like this:
UUID=theuuid /mnt/freeagent ext3 defaults,errors=remount-ro 0 1

---

### Post by blueturtl on 2008-09-18
Awfully quiet. Guys I meant to install Ubuntu, but the text mode installer always fails at partitioning faze for some reason and Debian "just worked" so I went with it instead. 8-[

---

### Post by fsmithred on 2008-09-18
You could try putting a mount command in /etc/rc.local. You might need to add some options. 

```
mount /dev/sda1 /mnt/freeagent
```

---

### Post by blueturtl on 2008-09-18
Thanks for the tip fsmithred, however getting the drive mounted is no longer the issue.

Now the issue is getting rid of the error fsck is spewing out every time the system is started. Otherwise it wouldn't really be an issue, but since it actually halts the entire boot process until I press Ctrl+D, I'd like to have it sorted out.

For referandum, fsck says something like this:

fsck.ext3: unable to resolve UUID (my disk's UUID)
fsck died with exit status 8

---

### Post by timcredible on 2008-09-18
you can mount a usb drive at boot, because i used to have ubuntu running exclusively off an external usb drive.  i found the instructions on how to do that from ubuntukids.org, so you might want to check there to see if that procedure could be applied to what you're trying to do.

---

### Post by Bucky Ball on 2008-09-19
Sorry, been studying. Sounds to me like the UUID is already in use or not available. Are you absolutely sure the UUIDs match? Can you get to the login screen or onto the desktop? Have you run recovery from the boot menu (second option) to see if that has thrown an error regarding this?

The other option is that the drive is not switched on perhaps when you are trying to boot (therefore it can't match the UUID in the /fstab with an exisiting UUID on the system). Or something to do with the system thinking that drive is already mounted therefore you can't use duplicate UUIDs (the one /fstab is trying to boot is already mounted and in use). Just some ideas.

Maybe try with the drive on at boot and find the error, then off at boot and find the error. Might be a clue in the comparison. :-k

---

### Post by blueturtl on 2008-09-19
Thank you for your time everyone!

Things just keep getting weirder and weirder. Today when I started the system up, everything went as I'm used to by now except that it was time to perform the scheduled checks on my internal hard-disks. I let the system do that, and then to my surprise it also started doing fsck on my external USB device! No error. Well at least until it got somewhere around 70%, and then bam:

> irq 3: nobody cared (try booting with the "irqpoll" option)
 [<c0131f0f>] __report_bad_irq+0x2b/0x69
 [<c01320d5>] note_interrupt+0x188/0x1bf
 [<c01318b3>] __do_IRQ+0x72/0xa1
 [<c0105073>] do_IRQ+0x43/0x50
 [<c0103a9a>] common_interrupt+0x1a/0x20
 [<c011855a>] __do_softirq+0x2c/0x75
 [<c01185c5>] do_softirq+0x22/0x26
 [<c0105078>] do_IRQ+0x48/0x50
 [<c0103a9a>] common_interrupt+0x1a/0x20
 [<c4a05e20>] usb_get_urb+0xc/0x10 [usbcore]
 [<c4a0562d>] hcd_submit_urb+0x10a/0x6ba [usbcore]
 [<c0105078>] do_IRQ+0x48/0x50
 [<c02750a4>] schedule+0x46e/0x4d2
 [<c02750a4>] schedule+0x46e/0x4d2
 [<c0105078>] do_IRQ+0x48/0x50
 [<c4a05df1>] usb_submit_urb+0x1bb/0x1de [usbcore]
 [<c4c517fd>] usb_stor_msg_common+0x92/0xe9 [usb_storage]
 [<c4c51bc7>] usb_stor_bulk_transfer_buf+0x39/0x64 [usb_storage]
 [<c4c520d5>] usb_stor_Bulk_transport+0x13f/0x207 [usb_storage]
 [<c4c52ce0>] usb_stor_control_thread+0x0/0x169 [usb_storage]
 [<c4c521b2>] usb_stor_invoke_transport+0x15/0x22c [usb_storage]
 [<c0111cba>] default_wake_function+0x0/0xc
 [<c4c52ce0>] usb_stor_control_thread+0x0/0x169 [usb_storage]
 [<c4c52ce0>] usb_stor_control_thread+0x0/0x169 [usb_storage]
 [<c4c52dda>] usb_stor_control_thread+0xfa/0x169 [usb_storage]
 [<c4c52ce0>] usb_stor_control_thread+0x0/0x169 [usb_storage]
 [<c4c52ce0>] usb_stor_control_thread+0x0/0x169 [usb_storage]
 [<c4c52ce0>] usb_stor_control_thread+0x0/0x169 [usb_storage]
 [<c0122b9c>] kthread+0xaf/0xdb
 [<c0122aed>] kthread+0x0/0xdb
 [<c0101005>] kernel_thread_helper+0x5/0xb
handlers:
[<c4a0529b>] (usb_hcd_irq+0x0/0x4a [usbcore])
[<c4a2b430>] (yenta_interrupt+0x0/0xac [yenta_socket])
[<c4a0529b>] (usb_hcd_irq+0x0/0x4a [usbcore])
[<c4a0529b>] (usb_hcd_irq+0x0/0x4a [usbcore])
[<c4a0529b>] (usb_hcd_irq+0x0/0x4a [usbcore])
Disabling IRQ #3

Then the hard-disk apparently goes offline because I get a whole bunch of IO errors and then finally fsck dies once again.

The system does continue to function normally, but I had to reboot to get the hard-disk back and then it's back to sameold:

> fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: Unable to resolve 'UUID=93b07048-2d30-4041-a9f2-10fcf6e9f998'
/dev/hdb3: clean, 578/378624 files, 45575/757063 blocks
fsck died with exit status 8

Buckyball, the hard-disk is a Seagate FreeAgent which powers on automatically during the boot sequence. In fact there is no way to turn it off manually. The fsck error about the UUID is weird because the UUID is correct (otherwise the drive couldn't mount at a later stage, right?).

Now I'm thinking this has to be a matter of detection, maybe the drive/uuid are simply not initialized by the time fsck is called to perform or something.

More disturbing though is the newly introduced kernel error about disabling IRQ 3. :confused: I did try to run fsck manually (after unmounting the disk of course) and it always leads to the drive going offline mid scan. Using the drive otherwise it seems perfectly fine.

I just love it when these things get out of control.

---

### Post by blueturtl on 2008-09-23
A solution to the original problem!

After some digging I came up with this solution.
Since apparently /dev/sda1 or UUID x is unavailable during the first runlevel automatic mounting should be done via the rc.local script.
To avoid the error append 'noauto' option to the fstab entry like so:

UUID=your disk's uuid /your/mountpoint ext3 defaults,errors=remount-ro,**noauto** 0 0

Then append the following to /etc/rc.local right before the line 'exit 0':

mount -U your disk's uuid

This should be perfectly usable in Ubuntu as well since Ubuntu and Debian are siblings. Thank you everyone for your time and input!

---

### Post by pentolino on 2008-11-29
Thanks to everyone, this also helped me; I' m trying to run Debian etch on my wii (yes, I mean it, on my Wii!) and got stuck at the same point: mount is called before usb are connected and thus mount fails.
Usin this trick at least I have them mount automatically at boot :-)

---

