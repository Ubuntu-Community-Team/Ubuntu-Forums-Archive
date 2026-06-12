---
title: "Canon pixma mg5620"
date: 2014-12-17
forum: Hardware
---

### Post by webusr1 on 2014-12-17
All,
I have a Canon PIXMA MG5620 with USB connection and can't get the printer to scan. I've tried using Simple Scan and installing Xsane, but neither of these two applications will recognize the printer for scanning. So, I trfied "scangearmp2-3.00-1-deb", but scangear does not fine any printers....

Note that I can print with no problems, but scan does not work... Oh, I forgot to say that I am running Ubuntu 14.04.

Any help would be greatly appreciated.

Best Regards.

---

### Post by pdc on 2014-12-19
so [COLOR="#0000FF"]ScanGearMP[/COLOR] is the programme Canon provide to run the scanner; so it has its own software;

[COLOR="#B22222"]Simple Scan[/COLOR] and [COLOR="#B22222"]XSane[/COLOR] use the open software programme sane to drive them; 

to run [COLOR="#0000FF"]ScanGearMP[/COLOR], one needs to type ```
scangearmp2
``` in a terminal; and hit the ENTER key;  as the programme you downloaded has the number 2 after scangearmp

________________________

did you do that?

---

### Post by col48 on 2014-12-19
I've got a PIXMA MG4250 running under 12.04.  The program which invokes a scan (from a Terminal) *for me* is scangearmp.  Like you, Simple Scan and xsane do not work for me.
Sometimes it cannot detect the scanner, but it is usually solved by a reboot.
Scanning and printing require different protocols, so the software is totally separate.

---

### Post by pdc on 2014-12-19
so Colin you would have downloaded [COLOR="#008000"]scangearmp-mg4200series-2.00-1-deb.tar.gz[/COLOR] and you can see the first part is [COLOR="#FF0000"]scangearmp[/COLOR]- so the command to run it is ```
scangearmp
```

_________________________________________

........whereas for the MG5620, the file one downloads is [COLOR="#008000"]scangearmp2-3.00-1-deb.tar.gz[/COLOR] and you can see it starts [COLOR="#FF0000"]scangearmp2[/COLOR]- so its command is ```
scangearmp2
```

_________________________________________

you report your 4200 series device is not seen by Simple Scan; curiously this link from the SANE project [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) says the MG4200 series is fully supported. If you type ```
lsusb
``` in a terminal, do you get > 04a9:1751

____________

this is the link for the sane-pixma that handles Canon devices [http://www.sane-project.org/man/sane-pixma.5.html](http://www.sane-project.org/man/sane-pixma.5.html)

---

### Post by col48 on 2015-01-10
Hi pdc
(1) I'm not Colin!
(2) I was simply trying to be encouraging by saying scangearmp works for me - I'm not trying to solve a problem for myself.
(3) a key observation for me may be that I am accessing the device through a router, ie computer - wire- router - wireless - scanner.  Therefore(?) lsusb does not see the device at all.  Perhaps that is the obstacle for SimpleScan. (No need to answer that!)
Hope this explains my slow response - I didn't look on the forum because I wasn't looking for an answer!

---

