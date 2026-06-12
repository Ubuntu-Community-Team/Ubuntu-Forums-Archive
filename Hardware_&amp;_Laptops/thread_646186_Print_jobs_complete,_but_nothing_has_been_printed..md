---
title: "Print jobs complete, but nothing has been printed."
date: 2007-12-20
forum: Hardware &amp; Laptops
---

### Post by Col-1023 on 2007-12-20
I have a Brother MFC 210C USB printer hooked up to my Ubuntu Gutsy via the usb cable.

I have my gutsy box connected to a router which also has an xp box connected to the same router.

I have set up the printer and it is recognised by both systems.

I can scan using the 210c scanner with gutsy, and I can print with it from the xp box using samba.

when I try to print from gutsy, cups says the job is first processing, then completed, there are no error messages, and the job log refers to all (35 so far) jobs having been completed.

However not a thing has been printed, the printer doesn't do a thing, it just sits there (It is on of course).

It doesn't matter is its a smalll text file (17k) or a large A4 photo, the printer will just do nothing, while gutsy says the job has completed without a problem/

The printer is set as the default printer.

The jobs are not collecting in the print que, once the job is (supposedly) completed, the que is then empty.

Any help very much appreciated.

---

### Post by Col-1023 on 2007-12-22
bump

---

### Post by dvatalar on 2007-12-27
I'm encountering this same issue. Am currently searching the forums, but haven't seen an answer yet (unless my search-fu is poor today). Will keep an eye on this thread...

---

### Post by orro_xo on 2007-12-27
What is the URI for the printer?

---

### Post by Col-1023 on 2008-01-02
Sorry for my late reply.

The printer url is,

usb://Brother/MFC-210C

It's a usb printer.

I still have no idea why it won't print.

---

### Post by orro_xo on 2008-01-02
Hmmm. I had the same problem with my printer an epson but it was via network. The URL seems to be correct. Strange.

---

### Post by Bablefish on 2008-01-02
I have one very obvoius but dumb question, does your printer work when connected directly to your computer? If it doesn't it could be a driver issue.

---

### Post by Col-1023 on 2008-01-02
No that is the problem.

The printer works when I use another computer (wndows box) and print through the samba network.

But my linux box is directly connected by the usb cable to the printer, and it won't print.

There is no error messages, the job que says the job completed sucessfully, but absolutly nothing happens.

The printer is on and recognised by the computer.

---

### Post by hute37 on 2008-01-02
+1
exactly the same problem with an HP LaserJet 1020 (USB)

usb://HP/LaserJet%201020

power off/on and cups restart doen't help 

(reported online, jop print successful but nothing happens ...)

CUPS 1.3.2, Ubuntu 7.10 (Gutsy Gibbon), AMD64

i've upgraded 7.10 from 7.4 ...

my syslog reports:

 /usr/sbin/hplj1020: foo2zjs: Missing HP LaserJet 1020 firmware file /usr/share/foo2zjs/firmware/sihp1020.dl                                                                          
/usr/sbin/hplj1020: foo2zjs: ...read foo2zjs installation instructions and run ./getweb 1020       


Jan  3 02:53:41 tethys kernel: [ 2514.835983] audit(1199325221.738:18):  type=1503 operation="inode_pe
rmission" requested_mask="a" denied_mask="a" name="/dev/tty" pid=17444 profile="/usr/sbin/cupsd"      
Jan  3 02:53:50 tethys kernel: [ 2520.054670] audit(1199325230.567:19):  type=1503 operation="inode_pe
rmission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=17462 profile="/usr/sbin/cupsd"    
Jan  3 02:53:50 tethys kernel: [ 2520.076424] audit(1199325230.591:20):  type=1503 operation="inode_pe
rmission" requested_mask="rw" denied_mask="rw" name="/dev/tty" pid=17465 profile="/usr/sbin/cupsd"    
Jan  3 02:53:50 tethys foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p9 -s7 -m1 -n1         
Jan  3 02:53:52 tethys foo2zjs-wrapper: gs -sPAPERSIZE=a4 -g9920x7016 -r1200x600 -sDEVICE=pbmraw -dCOL
ORSCREEN                                                                                              
Jan  3 02:53:52 tethys foo2zjs-wrapper: foo2zjs -r1200x600 -g9920x7016 -p9 -m1 -n1 -d1 -s7 -z1  -u 192
x96 -l 192x96 -L 0     -P                                                                             
                                               

Enabled CUPS debug log, but nothing interesting (for me)  is there, everything looks good. Only warnings are:


...
D [03/Jan/2008:02:57:54 +0100] [Job 35] perl: warning: Setting locale failed.                         
D [03/Jan/2008:02:57:54 +0100] [Job 35] perl: warning: Please check that your locale settings:        
D [03/Jan/2008:02:57:54 +0100] [Job 35] LANGUAGE = (unset),                                           
D [03/Jan/2008:02:57:54 +0100] [Job 35] LC_ALL = (unset),                                             
D [03/Jan/2008:02:57:54 +0100] [Job 35] LANG = "en_US"                                                
D [03/Jan/2008:02:57:54 +0100] [Job 35] are supported and installed on your system.                   
D [03/Jan/2008:02:57:54 +0100] [Job 35] perl: warning: Falling back to the standard locale ("C").  

...

D [03/Jan/2008:02:57:55 +0100] [Job 35] Pondering option 'job-uuid=urn:uuid:78b66e89-beb2-3e04-429a-d8
e76d9ad17d'                                                                                           
D [03/Jan/2008:02:57:55 +0100] [Job 35] Unknown option job-uuid=urn:uuid:78b66e89-beb2-3e04-429a-d8e76
d9ad17d.           

...

D [03/Jan/2008:02:57:56 +0100] [Job 35] Read 1024 bytes of print data...                              
D [03/Jan/2008:02:57:56 +0100] Discarding unused printer-state-changed event...     
D [03/Jan/2008:02:57:56 +0100] Discarding unused printer-state-changed event...                       
D [03/Jan/2008:02:57:56 +0100] Discarding unused printer-state-changed event...                       
D [03/Jan/2008:02:57:56 +0100] [Job 35] Wrote 1024 bytes of print data...                             
D [03/Jan/2008:02:57:56 +0100] [Job 35] Read 8192 bytes of print data...                              

...

D [03/Jan/2008:02:57:57 +0100] [Job 35] KID3 finished                                                 
D [03/Jan/2008:02:57:57 +0100] [Job 35] Wrote 3896 bytes of print data...                             
D [03/Jan/2008:02:57:57 +0100] [Job 35] Renderer process finished                                     
D [03/Jan/2008:02:57:57 +0100] [Job 35]                                                               
D [03/Jan/2008:02:57:57 +0100] [Job 35] Closing foomatic-rip.                                         
D [03/Jan/2008:02:57:57 +0100] PID 17536 (/usr/lib/cups/filter/foomatic-rip) exited with no errors.   
D [03/Jan/2008:02:57:57 +0100] PID 17537 (/usr/lib/cups/backend/usb) exited with no errors.           
D [03/Jan/2008:02:57:57 +0100] [Job 35] File 0 is complete.                                           
I [03/Jan/2008:02:57:57 +0100] [Job 35] Completed successfully.                                       
D [03/Jan/2008:02:57:57 +0100] Discarding unused printer-state-changed event...                       
D [03/Jan/2008:02:57:57 +0100] Discarding unused job-completed event...                               
D [03/Jan/2008:02:57:58 +0100] [Job 35] Unloading...                                                  
1
...

---

### Post by halw on 2008-01-02
Have you tried [CUPS]("http://localhost:631/") in your web browser to see if the printer is there or to set it up that way.

Don't know if this is the answer or not, just something else to try.

---

### Post by orro_xo on 2008-01-03
Yes. Try to set it up directly via CUPS [http://localhost:631/admin](http://localhost:631/admin). But it should work if you have the correct drivers. and the URL seems to be fine. Very strange but try vis CUPS is also my recomendation. That was how I managed to be able to connect my printer via a router. Is it possible to connect the printer to the router that you have?

---

### Post by blakegrover on 2008-01-03
I am having the same issues.  I have 5 different printers setup.  One is directly connected through usb and then 4 others are setup on the network.  I can print fine to all printers on other computers and all printers were working just fine a week ago.  I think there was an update I installed that caused this.  Every time I print it shows it printed correctly in linux but the printer doesn't do anything.  

One thing I noticed with a HP Color Laser printer is it showed it receiving data and then it went back to the online screen, as if it sent something to the printer but the printer didn't understand it.

Blake

---

### Post by blakegrover on 2008-01-03
I went into the cups interface through the web browser and all the printers worked by doing a print test page from the web interface but if I try to do it from the gui interface in System -> Administration -> Printing and doing a print test page it doesn't print but the computer thinks it printed, any suggestions?

Blake

---

### Post by popch on 2008-01-03
> **hute37 said:**
> 
my syslog reports:

 /usr/sbin/hplj1020: foo2zjs: Missing HP LaserJet 1020 firmware file /usr/share/foo2zjs/firmware/sihp1020.dl                                                                          
/usr/sbin/hplj1020: foo2zjs: ...read foo2zjs installation instructions and run ./getweb 1020       


It is not unreasonable to assume that the first two lines of your syslog state the problem. If the printer needs a firmware file for printing, and the firmware file is missing, then presumably the printer can not print.

Your printer installation or setup appears to be incomplete, or perhaps your printer is not supported.

If that is so, you could read the installation instructions for foo2zjs and run ./getweb 1020, as suggested by the second line.

---

### Post by Col-1023 on 2008-01-03
When I first started having this problem, after i upgraded from ubuntu 7.4 to 7.1, I tried many methods, one of which was to acces cups through the browser.

It also says the jobs complete, while nothing happens.

Checking the log shows that about 43 jobs have supposedly completed, but none of them worked.

Printing a test page via cups has no effect either.

Cups starts off with the printer being idle, then processing, then job completed, while the printer just sits there doing nothing (its turned on and recognised).

---

### Post by littleblackdot on 2008-01-03
popch,

i'm having the same problem with my hp laserjet 1020. i checked my system log and apparently i'm missing the firmware file.
i'm still pretty new to ubuntu and i was wondering if you could tell me how to run ./getweb 1020.
thanks.

---

### Post by popch on 2008-01-04
> **littleblackdot said:**
> popch,

i'm having the same problem with my hp laserjet 1020. i checked my system log and apparently i'm missing the firmware file.
i'm still pretty new to ubuntu and i was wondering if you could tell me how to run ./getweb 1020.
thanks.

Please understand that I have no similar printer to yours, and that I therefore can not verify if that command does anything at all. However, I would try to run it as follows:

```
Open a Terminal (click on the menu Applications/Accessories/Terminal)
Click once into the new window, then type
./getweb 1020
Press the enter key.
```

---

### Post by orro_xo on 2008-01-05
I have searched the HP website to try to find the hp drivers but i couldnt find ones for your printer for linux. One thing you could try though is to "Add/Remove programs" and search for "HP" (all software) and install the HPLIP Tolbox if you havent done it previously.

---

### Post by Val_0 on 2008-01-09
I have the same issue. I followed the instructions from [www.foo2zjs.com](www.foo2zjs.com) on how to install my HP LaserJet 1020. Using cups through web interface I can recognize the printer, add it and send a test page to print but nothing prints out. I checked the error log and there are no errors. All the jobs are completed successfully yet nothing is printed. I just finished converting my g/f and her laptop from XP to Ubuntu but I can't get this printer to work. Any help will be much appreciated.

---

### Post by Val_0 on 2008-01-09
Sorry the proper link is: [http://foo2zjs.rkkda.com/](http://foo2zjs.rkkda.com/)

After following the instructions and UNPLUGGING and REPLUGGING the USB printer cable everything worked and it now prints/

---

