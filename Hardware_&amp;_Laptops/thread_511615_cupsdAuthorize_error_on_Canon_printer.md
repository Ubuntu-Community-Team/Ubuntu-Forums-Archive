---
title: "cupsdAuthorize error on Canon printer"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by Timtro on 2007-07-28
Hi all,

I'm trying to get my Canon MP600 working. It's been quite a trip. I wish I had simply followed the instructions given in [http://ubuntuforums.org/showthread.php?t=456751](http://ubuntuforums.org/showthread.php?t=456751) . I think my problem may be that I screwed something along the way.

At some point, I tried install TurboPrint, thinking that I could print draft quality as it says on the website. Everything worked fine. I used ipp protocol to print to my MP600 on a Linksys WPS54G print server. That stupid software however put watermarks on all of my documents, making it useless to me. The software is far too overpriced to consider buying it but with all of  the trouble it has caused, I would feel little remorse in pirating it [-( . On that note, I removed it, but it seems that it may have broken something (but perhaps not).

Thinking that I could compare the Canon drivers to the TurboPrint, I tried following the directions given in the translated Japanese post here: [http://ubuntuforums.org/showthread.php?t=456751](http://ubuntuforums.org/showthread.php?t=456751) (same as above.)
I don't think I got it to work properly before I uninstalled TurboPrint (using synaptic). That's when I started having real problems.

When I made the printer, it was paused saying that it could not find the filter:
```
Paused: Filter "pstocanonij" for printer... No such file or directory
```
NB: I may have paraphrased this message slightly. Although the overall insanity is preserved, it would have been nice for someone searching the error message to pick up on.

Anyway, I forced the issue and I received no complaints. Under the printer properties, I was told that it had connected to the printer at was ready to print. I tried a test page, and it doesn't go through. I turned on the debug mode, and here is the junk I got from the log:

```

...
E [28/Jul/2007:01:47:50 -0400] cupsdAuthorize: Local authentication certificate not found!
D [28/Jul/2007:01:47:50 -0400] CUPS-Get-Printers
D [28/Jul/2007:01:47:50 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [28/Jul/2007:01:47:50 -0400] cupsdReadClient: 8 POST / HTTP/1.1
E [28/Jul/2007:01:47:50 -0400] cupsdAuthorize: Local authentication certificate not found!
D [28/Jul/2007:01:47:50 -0400] Get-Printer-Attributes ipp://localhost/printers/MP600-Ver.2.70
D [28/Jul/2007:01:47:50 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [28/Jul/2007:01:47:52 -0400] cupsdReadClient: 8 POST / HTTP/1.1
E [28/Jul/2007:01:47:52 -0400] cupsdAuthorize: Local authentication certificate not found!
D [28/Jul/2007:01:47:52 -0400] CUPS-Get-Printers
D [28/Jul/2007:01:47:52 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [28/Jul/2007:01:47:52 -0400] cupsdReadClient: 8 POST / HTTP/1.1
E [28/Jul/2007:01:47:52 -0400] cupsdAuthorize: Local authentication certificate not found!
D [28/Jul/2007:01:47:52 -0400] Get-Printer-Attributes ipp://localhost/printers/MP600-Ver.2.70
D [28/Jul/2007:01:47:52 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [28/Jul/2007:01:47:52 -0400] cupsdReadClient: 8 POST / HTTP/1.1
E [28/Jul/2007:01:47:52 -0400] cupsdAuthorize: Local authentication certificate not found!
...

```

I've reinstalled the drivers several times, and remade the printer. Same error. Does anyone know what is wrong?

Thanks a million!

---

### Post by ronny_d on 2007-07-30
> **Timtro said:**
> Hi all,

I'm trying to get my Canon MP600 working. It's been quite a trip. I wish I had simply followed the instructions given in [http://ubuntuforums.org/showthread.php?t=456751](http://ubuntuforums.org/showthread.php?t=456751) . I think my problem may be that I screwed something along the way.

At some point, I tried install TurboPrint, thinking that I could print draft quality as it says on the website. Everything worked fine. I used ipp protocol to print to my MP600 on a Linksys WPS54G print server. That stupid software however put watermarks on all of my documents, making it useless to me. The software is far too overpriced to consider buying it but with all of  the trouble it has caused, I would feel little remorse in pirating it [-( . On that note, I removed it, but it seems that it may have broken something (but perhaps not).

Thinking that I could compare the Canon drivers to the TurboPrint, I tried following the directions given in the translated Japanese post here: [http://ubuntuforums.org/showthread.php?t=456751](http://ubuntuforums.org/showthread.php?t=456751) (same as above.)
I don't think I got it to work properly before I uninstalled TurboPrint (using synaptic). That's when I started having real problems.

When I made the printer, it was paused saying that it could not find the filter:
```
Paused: Filter "pstocanonij" for printer... No such file or directory
```
NB: I may have paraphrased this message slightly. Although the overall insanity is preserved, it would have been nice for someone searching the error message to pick up on.

Anyway, I forced the issue and I received no complaints. Under the printer properties, I was told that it had connected to the printer at was ready to print. I tried a test page, and it doesn't go through. I turned on the debug mode, and here is the junk I got from the log:

```

...
E [28/Jul/2007:01:47:50 -0400] cupsdAuthorize: Local authentication certificate not found!
D [28/Jul/2007:01:47:50 -0400] CUPS-Get-Printers
D [28/Jul/2007:01:47:50 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [28/Jul/2007:01:47:50 -0400] cupsdReadClient: 8 POST / HTTP/1.1
E [28/Jul/2007:01:47:50 -0400] cupsdAuthorize: Local authentication certificate not found!
D [28/Jul/2007:01:47:50 -0400] Get-Printer-Attributes ipp://localhost/printers/MP600-Ver.2.70
D [28/Jul/2007:01:47:50 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [28/Jul/2007:01:47:52 -0400] cupsdReadClient: 8 POST / HTTP/1.1
E [28/Jul/2007:01:47:52 -0400] cupsdAuthorize: Local authentication certificate not found!
D [28/Jul/2007:01:47:52 -0400] CUPS-Get-Printers
D [28/Jul/2007:01:47:52 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [28/Jul/2007:01:47:52 -0400] cupsdReadClient: 8 POST / HTTP/1.1
E [28/Jul/2007:01:47:52 -0400] cupsdAuthorize: Local authentication certificate not found!
D [28/Jul/2007:01:47:52 -0400] Get-Printer-Attributes ipp://localhost/printers/MP600-Ver.2.70
D [28/Jul/2007:01:47:52 -0400] cupsdProcessIPPRequest: 8 status_code=0 (successful-ok)
D [28/Jul/2007:01:47:52 -0400] cupsdReadClient: 8 POST / HTTP/1.1
E [28/Jul/2007:01:47:52 -0400] cupsdAuthorize: Local authentication certificate not found!
...

```

I've reinstalled the drivers several times, and remade the printer. Same error. Does anyone know what is wrong?

Thanks a million!

Hi, first of all: you only had the 'testversion' of Turboprint and that is why it printed their logo on your pages... 

Second: did you download rpm stuff and is your version Ubuntu (which "brand"?), or...?

---

### Post by ronny_d on 2007-07-30
p.s.: i mean just if you downloaded an rpm, just in case, so only if so (else i am wrong) you have to know that rpm means "red hat package manager" and is from 'red hat'  and "red hat" is another Linux distro ("distribution"); if so you use Ubuntu (which one?), it is Debian based... (Debian so is again another "distro" of Linux...). 

Sometimes, as i have read here and there, people use command like 'alien' in Ubuntu to "assimllate" rpm to debian suited source (for Ubuntu, but then you must check your specific Ubuntu "brand" / distro...), and if so this is true,  this "alien" command could work for the driver you need, but anyway best is to find the debian package for that specific driver (if you work on Ubuntu and check your Ubuntu-distro) and else... find the exact command "alien" you than have to do in sudo, as far as i remember it is something like sudo alien -k naamofthefileoftheRPM-file.rpm, just the name of that rpm anyway..., but find this command else somewhere at this forum if it exists, then you know for sure, and for sure a little Internet research could maybe help you too for finding the debian based driver possibility if it exists...  

[http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600](http://openprinting.org/show_printer.cgi?recnum=Canon-PIXMA_MP600)

i guess is only for rpm, if i am not wrong. I am not sure if the "alien" command in sudo is generally working to make it "debian";  i would recommend to  try to find this information, if it exists, on the Internet or somewhere else at this Ubuntuforums.

---

### Post by ronny_d on 2007-07-30
... And...: if you succeed with "researching" the situation in your case about the validity (or not) of the "alien" command, and so if it would be true / "correct" what i wrote here about that 'alien' command (its syntax), then... when such would work, it could be useful to reboot your machine first before testpage tryout, et cetera, though if the printer is usb connection 'reboot' would not be necessary; but just in case it would be no usb but parallel: reboot first. Anyway do not forget Ubuntu is Debian based, not RedHat based, so you can not "just like that" use rpm for Ubuntu.

---

### Post by Timtro on 2007-08-01
Thanks,

I was out of town for a bit, sorry for the late reply.

I'm using Ubuntu. I used alien to convert the rpms to debs. The only concern may be the scripts id the rpms, but this should be a problem with the --scripts flag to alien. Of course, scripts are not always portable, but since other confirm this to work in Ubuntu, I would not expect problems.  That being said, I'm using the latest Feisty.

I'll look into this more. If anyone has suggestions, please post. If not, I'll post when I find the solution.

Cheers,



Tim.

---

