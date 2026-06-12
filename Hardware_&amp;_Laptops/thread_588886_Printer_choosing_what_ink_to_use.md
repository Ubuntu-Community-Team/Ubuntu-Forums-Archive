---
title: "Printer choosing what ink to use?"
date: 2007-10-23
forum: Hardware &amp; Laptops
---

### Post by shadowhywind on 2007-10-23
Hi all I have been having this problem for a few weeks now, and coming up with no ideas on how to fix it. 
The Issue: When i print Everything is green or Blue, I found a fix, in the printer settings -> Instances -> Driver Settings -> Printerout Mode If i set it to Normal  Grayscale (Black catridge) i can use the black ink. But then I can't use the color ink. Any one have any ideas? ! 

I am running kubuntu 7.10 amd64 
Printer is an hp PSC 120 all in one.

---

### Post by csseurg6 on 2007-10-23
hi, i have a similar problem, and i report the bug on launchpad, and i think that we have a serious bug in HP Linux program.

---

### Post by shadowhywind on 2007-10-24
The odd part is I just connected to another HP printer on the network (which is connected to a Win XP). Somehow the network drivers work perfectly fine

---

### Post by shadowhywind on 2007-10-24
I fixed the printer issues!!!!! I stumbled across the printer config files and decided to take a small peak inside of them and found a possible solution. I used the network printer that was working as a guide, What i did was i copied the code that was under *OpenGroup: General/General and put it into my local printer that wasn't working. and So far Everything is working great! I can not be 100% if all is working since i am completely sure that i am out of red. But doing the test page, I have yellow blue, green and Black, all on one page!!!!  I will post the code that i used just in case you don't have a network printer you can steal it from. The file that should be changed is /etc/cups/ppd/<printer name>.ppd you do need root privilege, also make sure you make a backup just incase. But give it a try and hopefully this works. You might also compare the two and see what is the difference, and change what needs to be changed. Hope this helps

```

*OpenGroup: General/General

*OpenUI *PrintoutMode/Printout Mode: PickOne
*FoomaticRIPOption PrintoutMode: enum Composite B
*OrderDependency: 10 AnySetup *PrintoutMode
*DefaultPrintoutMode: Normal
*PrintoutMode Draft/Draft (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Draft"
*FoomaticRIPOptionSetting PrintoutMode=Draft: "Quality=300FastDraftCol&&
orCMYK"
*End
*PrintoutMode Draft.Gray/Draft Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Draft.Gray"
*FoomaticRIPOptionSetting PrintoutMode=Draft.Gray: "Quality=300FastDra&&
ftGrayscaleCMYK"
*End
*PrintoutMode Normal/Normal (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Normal"
*FoomaticRIPOptionSetting PrintoutMode=Normal: "Quality=300ColorCMYK"
*PrintoutMode Normal.Gray/Normal Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=Normal.Gray"
*FoomaticRIPOptionSetting PrintoutMode=Normal.Gray: "Quality=300Graysc&&
aleCMYK"
*End
*PrintoutMode High/High Quality (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=High"
*FoomaticRIPOptionSetting PrintoutMode=High: "Quality=600ColorCMYK"
*PrintoutMode High.Gray/High Quality Grayscale (auto-detect paper type): "%% FoomaticRIPOptionSetting: PrintoutMode=High.Gray"
*FoomaticRIPOptionSetting PrintoutMode=High.Gray: "Quality=600Grayscal&&
eCMYK"
*End
*PrintoutMode Photo/Photo (on photo paper): "%% FoomaticRIPOptionSetting: PrintoutMode=Photo"
*FoomaticRIPOptionSetting PrintoutMode=Photo: "Quality=1200PhotoCMYKFu&&
llBleed"
*End
*CloseUI: *PrintoutMode


```

---

