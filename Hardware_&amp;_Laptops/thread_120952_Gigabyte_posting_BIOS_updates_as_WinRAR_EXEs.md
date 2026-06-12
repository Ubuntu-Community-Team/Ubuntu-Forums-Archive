---
title: "Gigabyte posting BIOS updates as WinRAR EXEs"
date: 2006-01-23
forum: Hardware &amp; Laptops
---

### Post by yetanothersteve on 2006-01-23
I wanted to update the BIOS on my motherboard before ordering a new cpu that would require the BIOS update. (No point ordering the cpu if the BIOS update fails.)

I downloaded the only BIOS update I could find and it was in EXE format. 

Not having a windows machine at home, I googled for what to do and came up with try unzip or wine. Wine seemed liked overkill, so I tried unzip.

```
zippy@u386:~/data1$ unzip bios_k8ns939_f8.exe
Archive:  bios_k8ns939_f8.exe
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
unzip:  cannot find zipfile directory in one of bios_k8ns939_f8.exe or
        bios_k8ns939_f8.exe.zip, and cannot find bios_k8ns939_f8.exe.ZIP, period
```

Dosbox did not work either, as the EXE requires 32bit mode to run.

Ok, now I'm ticked, so I broke down and installed wine and configured it with winecfg. Running with wine.

```
zippy@u386:~/data1$ wine bios_k8ns939_f8.exe

```

Which pops open a Winrar Self Extracting Archive dialog box. Wouldn't a SFX created with Winzip or PKZip have been easier for both creator and consumer?
The wine works fine and I now have the contents of the archive.

Now that I know they are Winrar SFX's, I experimented by installing unrar-nonfree through synaptic.

```
zippy@u386:~/data1$ unrar e bios_k8ns939_f8.exe

RAR 3.30    Copyright (c) 1993-2004 Eugene Roshal    22 Jan 2004
Shareware version         Type RAR -? for help


Extracting from bios_k8ns939_f8.exe

Extracting  K8NS939.F8                                                OK
Extracting  autoexec.bat                                              OK
Extracting  FLASH891.EXE                                              OK
All OK

```

Might also work with the free version of unrar but did not feel like testing it.

Then, I formatted a floppy, copied the K8NS939.F8 file to it, and rebooted into my bios where luckily there is flash utility built into the bios and I did not have to create a Freedos diskette. Flash worked and now I can order cpu.

I also submitted a question to Gigabyte tech support asking why they do not distribute their Bios updates in a friendlier format, like Zip.

---

### Post by matthew on 2006-01-23
[quote=yetanothersteve]I also submitted a question to Gigabyte tech support asking why they do not distribute their Bios updates in a friendlier format, like Zip.[/quote]Wow, how frustrating. I'm glad to hear you were able to figure it out, though! I think contacting Gigabyte is the best thing to do--they really need to know that they are shutting Linux users out (or at least making their lives very difficult). Good job.

---

### Post by yetanothersteve on 2006-01-25
I received a response from Gigabyte, although I find it to be a poor response. They really should distribute their files in an easier to decompress format. Even a Winzip created self extracting archive would have been preferable, because at least those are readable by the open source and free unzip utility.

[INDENT]
Answer : 	Hello

We have attached you just the bios file, please copy it onto a floppy and use q-flash to update the bios. This bios is for the K8NS 939 motherboard version F9 which is the latest version available.

Thank you

Attachment : 	k8ns939.f9 ( 256 KB ) :[/INDENT]

---

### Post by yetanothersteve on 2006-01-26
Here was my response:

[INDENT]For your information, I was able to decompress the Winrar self extracting executables that Gigabyte is using to archive the bios and related files. The executable ran fine using wine and also decompressed using unrar. I believe that most people downloading the bios archive executables would expect them to be Winzip self extracting executables and not Winrar. If winzip had been used, my first attempt, by using unzip, would have been successful, and I would never have had to post a tech support question.[/INDENT]

And Gigabyte's response to me:

[INDENT]No problem[/INDENT]

I work in IT and relish giving a flip answer, but I try to reserve it for other people in the IT areas and not go out of my way to annoy the folks who pay our bills. 

My final comment: I hope Gigabyte at least paid for their copy of Winrar.

---

### Post by bernardfrancois on 2006-04-12
[QUOTE=yetanothersteve]
Might also work with the free version of unrar but did not feel like testing it.
[/QUOTE]

I can confirm that it also works with the free version (which I downloaded from rarlabs.com).
I had to extract a winrar exe with microsoft office, downloaded legally trough MSDNAA (I need it to do vbscripting with excel for school and I wanted to burn it to a disc to be able to access it from within vmware player).

---

