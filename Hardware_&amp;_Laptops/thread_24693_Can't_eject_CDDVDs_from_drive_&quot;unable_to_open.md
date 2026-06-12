---
title: "Can't eject CD/DVDs from drive: &quot;unable to open /dev/hd*&quot;"
date: 2005-04-08
forum: Hardware &amp; Laptops
---

### Post by valthonis on 2005-04-08
Don't know if anyone else has had this exact problem.  I've scoured the forum with the search engine and found plenty of similar issues, but not this one.  I'm running Hoary (fully updated as of 2 AM EDT, 4/8/05), and I had an issue with my optical drive.  I was completely unable to get discs to automount on insert, and equally unable to unmount or eject them without resorting to the command line.  By following the advice [here](http://www.ubuntuforums.org/showthread.php?t=20982) , I was able to restore automount functionality and Nautilus successfully unmounts optical volumes as well.  There is still the issue of having the disc eject once it is unmounted.  So far I'm unable to eject via software and resort to using the eject button on the drive itself.

I suppose this isn't that big a deal (I'm not so lazy that I can't hit the eject button mere inches away) but, being a big Linux proselytizer I frequently use my machine as a showpiece convincing people fed up with Windows to give Ubuntu a try.  Having everything work seamlessly is everything to image-conscious Windows users, so something as basic as ejecting one's optical media can spoil the slick image Ubuntu projects so well.

Has anyone else out there encountered this problem and, if so, conquered it?

Thanks in advance,
valthonis

P.S. - There IS an error message that Nautilus throws when I right-click on the optical volume and choose "Eject": "Unable to eject media."  Under "Show more details, it says: "eject: unable to open `/dev/hdc`"  As you may have guessed, /dev/hdc is my optical drive.

---

### Post by valthonis on 2005-04-08
OK, after some frantic tinkering, I believe I've stumbled across a solution.  When I achieved partial results after adding the user *hal* to group *disk*, I decided to head on into Synaptic and reinstall the hal package and all its dependencies.  Once done, I rebooted and **WHAM!**, all is right with the world again.  I have full software eject as well as automount capability, and without having to resort to the kind of CLI jockeying that turns away the Windows folk I try to enlighten.  (Nothing is wrong with command line, mind you.  I've been using it forever.  But you know how the Windows folk are.)

Hope this can help some other poor soul out there with this problem.

---

### Post by niutonas on 2005-05-18
Hi,

i have simillar problem to on old Thinkpad i1400 (1621-467)
running hoary 5.04.

Begining was that that on XFCE i can't play audio cd but can ripp
with sound juicer tracks without problem.

But totem player was giving something like:
can't read "cdda" or can't found "cdda"
cd play was not playing too.

But there is no problem when i am on gnome.
And totem and cd play can play audio cds.
Totem is doing it a little better than cd play.
Cd play makes every 1~2 secons short pause.
There is no such problem with totem.
   
So i switch from xfce to gnome.
And after some have problem:

Unable to eject media
more details:
eject: unable to eject, last error: Invalid argument

and blocked cd/dvd rom :)

then i desided to look at "dmesg" output as root:

=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 1067348
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 1066324
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100

*************** a lot such kind I/O errors************
*************** at the end **************

end_request: I/O error, dev hdc, sector 56
Buffer I/O error on device hdc, logical block 7
hdc: command error: status=0x51 { DriveReady SeekComplete Error }
hdc: command error: error=0x51
ide: failed opcode was 100
end_request: I/O error, dev hdc, sector 0
Buffer I/O error on device hdc, logical block 0
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO
program eject is using a deprecated SCSI ioctl, please convert it to SG_IO


a long story :)
but may be it will be usefull for some developers :)

So i am going to kill some proccess or restart :)

MMMM can't kill kblocd/0 event  as root  ](*,) 
so restart 

Many Thanks for any comment.

---

### Post by pb7804 on 2005-06-17
Niutonas, I have exactly the same thing about eject. It works though when drive is empty but when there is media inserted it doesn't. I got it unmounted, yes, but not ejected. What can we do except to use sudo eject from command line? I don't know yet.

By the way, from command line eject works only under sudo and only with **-s** switch specified (scsi mode), but error message is displayed anyway.

---

