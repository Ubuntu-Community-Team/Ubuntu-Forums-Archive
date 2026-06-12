---
title: "Burning multiple CDs at once"
date: 2008-11-22
forum: General Help
---

### Post by wd5gnr on 2008-11-22
I have several PCs with between 2 and 4 CD recorders on them. I make data CDs en masse using these boxes and I prefer to use both (or all 4) recorders at once. Nero does this in Windows (but not Nero4Linux) and I've used other software that does it.

I wrote a script to just run two copies of wodim and it DOES work. Sometimes. And sometimes it gives me things like:


Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error                
CDB:  2A 00 00 00 04 3D 00 00 1F 00                                           
status: 0x2 (CHECK CONDITION)                                                 
Sense Bytes: 72 0B 00 00 00 00 00 0E 09 0C 00 00 00 02 00 00                  
Sense Key: 0x0 No Additional Sense, Segment 11                                
Sense Code: 0x00 Qual 0x02 (end-of-partition/medium detected) Fru 0x0         
Sense flags: Blk 0 (not valid)                                                
cmd finished after 51.482s timeout 40s                                        
/usr/bin/wodim: A write error occured.                                        
/usr/bin/wodim: Please properly read the error message above.                 
Errno: 5 (Input/output error), write_g1 scsi sendcmd: no error                
CDB:  2A 00 00 00 00 1F 00 00 1F 00                                           
status: 0x2 (CHECK CONDITION)                                                 
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 21 02 00 00                  
Sense Key: 0x5 Illegal Request, Segment 0                                     
Sense Code: 0x21 Qual 0x02 (invalid address for write) Fru 0x0                
Sense flags: Blk 0 (not valid)                                                
cmd finished after 50.859s timeout 40s                                        
/usr/bin/wodim: The current problem looks like a buffer underrun.             
/usr/bin/wodim: It looks like 'driveropts=burnfree' does not work for this drive.                                                                           
/usr/bin/wodim: Please report.                                                
/usr/bin/wodim: Make sure that you are root, enable DMA and check your HW/OS set up.                                                                        
Errno: 5 (Input/output error), close track/session scsi sendcmd: no error     
CDB:  5B 00 02 00 00 00 00 00 00 00                                           
status: 0x2 (CHECK CONDITION)                                                 
Sense Bytes: 70 00 05 00 00 00 00 0A 00 00 00 00 72 03 00 00                  
Sense Key: 0x5 Illegal Request, Segment 0                                     
Sense Code: 0x72 Qual 0x03 (session fixation error - incomplete track in session) Fru 0x0                                                                   
Sense flags: Blk 0 (not valid)                                                
cmd finished after 0.002s timeout 480s                                        
cmd finished after 0.002s timeout 480s    

Followed by many other errors.

Any ideas on either a) why this may be, or b) Linux software that will burn to multiple recorders so I can ditch the script?

As it is now, I hate to use it because I get the occasional success and the occasional coaster.

Thanks.

---

### Post by lisati on 2008-11-22
I haven't actually tried recording two or more disks at once on any of my machines, I would hesitate to do so unless I invested some money in a specialised disk duplicator. 

A clue is provided by the reference to "underburn" in the error messages: this usually indicates that your machine wasn't able to provide enough data to one of the burners at the speed it needed it.

---

### Post by mbeach on 2008-11-22
reading through 
[http://www.linuxcertif.com/man/1/wodim/](http://www.linuxcertif.com/man/1/wodim/)

and wondering if  the following would make a difference
driveropt=noburnfree

is this an old drive?  from that man page:
burnfree
    Turn the support for Buffer Underrun Free writing on. This only works for drives that support Buffer Underrun Free technology, which is available on most drives manufactured in this millennium.

this guy has some pointers and some sample scripts probably much like your own - is is possible to slow down your burn with the speed flag?  
[http://www.linuxjava.net/howto/cddvd/](http://www.linuxjava.net/howto/cddvd/)

sorry to not give a true answer - dug around and couldn't find anything for multiple burning with linux other than with a script.

---

### Post by wd5gnr on 2008-11-23
No the drives are identical and newish. This works 100% fine under Windows and I have done it on many machines including this exact one. There is no reason it should not work under Linux. 

I'm going to play with some more options as you've suggested, but was looking to see if anyone else had any experience with it. I do think burnfree is on by default if the drive supports it (which it does) but I'll investigate further.

From the same man page:
This option is deprecated and is mentioned here for documentation purposes only. The BURN-Free feature is enabled by default if the drive supports it. However, use of BURN-Free may cause decreased burning quality. Therefore it can be useful to disable it for certain purposes, eg. when creating a master copy for mass CD production.

For completeness: I just added -immed to the command line of both wodim lines and had a successful burn. Of course, I've had success before too, so it will take some more time to determine if that was truly effective or not.

If anyone wants the script let me know. It does seem to work.

---

