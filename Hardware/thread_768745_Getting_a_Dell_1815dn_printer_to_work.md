---
title: "Getting a Dell 1815dn printer to work"
date: 2008-04-26
forum: Hardware
---

### Post by theacoustician on 2008-04-26
I'm running Hardy 64bit edition and am having a devil of a time trying to get my Dell 1815dn network printer to print anything.  I've tried installing with the instructions off Dell's website and, I'm not sure what I did, but it permanently pegged my CPU at 100% and failed to print a thing.  So if someone could point me to a moron's walk through or at least some things to try to get this working, it would be greatly appreciated.

---

### Post by Bjorg on 2008-08-07
I would also like to know howto get this printer to work with ubuntu x64 8.04. Thanks in advance.

---

### Post by theacoustician on 2008-08-07
> **Bjorg said:**
> I would also like to know howto get this printer to work with ubuntu x64 8.04. Thanks in advance.
I figured it out, but only the printing portion.  Fax and scanning is still not happening.  I don't fax much and I scan to an old USB drive I stuck in the printer and just move it over to my machine, so all in all, it works.

1. Go to Dell's website and download the SuSE drivers for this printer.

2. Uncompress the file and go to noarch->at_opt->share->ppd .  In that folder you should find a file called mfp1815ps.ppd.  This is the only file you need out of the whole package.

3. Now go to System->Administration->Printing.  Click new printer.  Select Internet Printing Protocol (ipp).  Put the IP address in the host field (just xxx.xxx.xxx.xxx, no prefixes).  Change queue to just / .  If you set everything correctly, you should be able to click the Verify button and it will confirm the printer is there.  When it asks for the driver, point it to the mfp1815ps.ppd file.

4. Print a test page and enjoy using your 1815dn in Linux :)

---

### Post by Bjorg on 2008-08-09
Thanks, thanks, thanks!!!!! :popcorn:

I have been may many time trying to set the printer to work.




I just want to add that the driver is here:
[http://ubuntuforums.org/showthread.php?t=501621](http://ubuntuforums.org/showthread.php?t=501621)

---

### Post by MourningWood on 2008-12-09
Your awesome!  Thanks a million :popcorn:

---

### Post by Bjorg on 2009-01-16
Thanks alot for the guide. I got it to work under Ubuntu!!

---

### Post by madmac63 on 2009-02-23
This worked perfectly for me.

Thanks!!!

---

### Post by rgarand3006 on 2010-01-11
Just ran through this install on my Kubuntu 9.10 x64 using the SuSE driver from the Dell website.  It worked like a champ.  Thanks everybody.

---

### Post by Josego on 2010-01-26
NETWORK SCANNING WITH THE DELL 1815DN.-

I want to share the solution that Jon Chambers gave to me.- 

Quote

You didn't mention with which operating system you wanted to use your 1815dn?

See [http://www.jon.demon.co.uk/dell1600n-net-scan/](http://www.jon.demon.co.uk/dell1600n-net-scan/)

This is the homepage for a perl scanner driver script that I wrote for the
Dell 1600n, to which support for the 1815dn was later added.  This should
work for any OS on which perl can run (linux, MacOS, windows, etc).

There is also a link to Dell's own drivers (although note that I have never
tried it out as I don't have an 1815dn).

No special drivers are required for printing under linux - the generic
postscript driver should work fine.  (Actually the same is true of 32 and 64
bit windows although the drivers are more confusingly named.)

Let me know how you get on.  Good luck!

cheers,

Jon

Unquote.


That works very well for me. Thanks Jon. 

I hope this works for everybody else.

Josego.-

---

### Post by clueblue on 2012-02-13
Thanks very much.

---

### Post by mbilauca on 2012-03-07
In Ubuntu 11.10 64bit I went Add printer > Network printer > Selected the DELL 1815dn and IPP network printer via DNS-SD and click Forward. It will search for drivers and eventually you are asked to select a PPD file. I pointed this at the PPD file that came in the Windows 7 driver from DELL. Printers works very well.

---

