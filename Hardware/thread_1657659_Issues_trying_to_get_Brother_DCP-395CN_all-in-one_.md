---
title: "Issues trying to get Brother DCP-395CN all-in-one working"
date: 2011-01-01
forum: Hardware
---

### Post by norfair on 2011-01-01
I bought the Brother DCP-395CN to replace my incompatible Canon printer, as I read that HP and Brother printers/all-in-ones were the most Linux friendly. I even checked before getting the DCP-395CN to make sure it could work, and found that Brother had a Linux driver available ([here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/download_prn.html#DCP-395CN")). However, in trying to set up the printer and installing the driver, I am given this message:

[INDENT]Error: Dependency is not satisfiable: dcp395cnlpr[/INDENT]

I have run all of the required commands Brother tells me ([here]("http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html")), and even installed everything Brother related via the Ubuntu software center.

I'm not the swiftest on troubleshooting things myself, as even after five years as an Ubuntu user, I'm still not sure of all of the who's, how's and what for's with respect to how things operate... Try as I might.

Is there anyone that might be able to offer some hearty chunks of wisdom my way, perhaps?

---

### Post by gordintoronto on 2011-01-01
You have marked the thread as "Solved." Perhaps you could tell us how it was solved?

---

### Post by perspectoff on 2011-01-01
I don't have that particular model, but I recently went through an exercise getting all the print/scan/fax functions of my Brother multifunction device (model 7820-N) working in (K)Ubuntu.

The steps are probably relatively similar to yours. I wrote them down:

Ubuntuguide.org at

[http://ubuntuguide.org/wiki/MFC-7820N](http://ubuntuguide.org/wiki/MFC-7820N)

and Kubuntuguide.org at

[http://kubuntuguide.org/MFC-7820N](http://kubuntuguide.org/MFC-7820N)

---

### Post by norfair on 2011-01-08
> **gordintoronto said:**
> You have marked the thread as "Solved." Perhaps you could tell us how it was solved?


Sorry... I didn't update my thread, as while my initial issue has been somewhat solved (in that the printer "works," but not fully), I didn't feel future posting would be of value to anyone. I think I am just doomed to never get a printer to work with Ubuntu - let alone an all-in-one. I never could print photos on my old Canon and Ubuntu 8.04, and now can't print photos or scan with Ubuntu 10.04 and my new Brother (that I bought specifically because HP and Brother are supposed to be Linux friendly, potentially working out of the box (HA!)). 

Anyway, how I solved my problem of getting my printer and my computer to communicate was to install both drivers. I thought I just needed the CUPS driver, not the LPR driver. I'm not sure why I thought that, but I did. Once I installed both, I was able to print. And by print I mean super basic text stuff. I still can't print photos or scan (despite downloading the drivers from Brother and successfully installing them). I have tried all that I know to try, but will continue to try through the weekend.

I just found this thread and will see if it will help:
[http://ubuntuforums.org/showthread.php?t=590793&page=32]("http://ubuntuforums.org/showthread.php?t=590793&page=32")

I also want to note that I was also severely struggling with getting CUPS to work at all. It never started at boot, and though it worked after starting it via the terminal, it always needed a restart - both on my old Canon, and now on my Brother (that it looks like I'll be returning). However, Morbius1 posted a script that fixed my CUPS issue when nothing else seemed to  work:
[http://ubuntuforums.org/showthread.php?t=1550539]("http://ubuntuforums.org/showthread.php?t=1550539")

So, hooray for at least one positive. Of course, what's the point of having CUPS working without having a fully functioning multifunction printer?

---

### Post by gordintoronto on 2011-01-08
I'm quite astonished that you are having trouble. I have a Brother network laser printer attached to my router. With recent versions of Ubuntu, I have simply opened Administration/Printing, selected "Add," let it find the printer (which took several seconds), and a couple of mouse clicks later it was working perfectly.

---

### Post by linuxonbute on 2011-01-09
I have a networked ( wireless ) Brother DCP585CW and have Ubuntu 10.04 on my laptop and 10.10 on my desktop PC. I went through the full set of instructions on the brother website and it works fine. One thing of note is that, on my laptop I did it in the order they said, but on the desktop I did it in a different order first time ( which didn't work ) then removed it all and did it again in the correct order and it then worked. This includes scanning as well, not just printing.

Is the printer a network printer or connected via USB?
i am puzzled as to how you can print 'simple' stuff but not photos and so on. 
Can you print text in colour or just black? 
Are you certain you downloaded the correct drivers? 
If it is networked are you sure you have a suitable network address for it, that you followed the instructions for a network printer and not the locally connected printer and that it is set up for the right paper size etc?

---

### Post by norfair on 2011-02-01
Thanks for your response. Yes, I do have my printer connected via USB and can print text in color, but still can't print decent photos. I hear the printer rev up, then make faint, but high pitched squealing sounds, then eventually spit out a blank piece of paper. What's odd, is that the printer icon in my panel bar that stays active until finished printing, disappears almost instantly when trying to print a picture in fine to photo quality. I can print a basic photo, but the quality is horrid. I know the printer I have isn't the best at photos, but I know it's more than capable. I know this, as I connected my camera to the printer to print a picture and it came out great. I just can't get the printer and my computer to play nice. Very strange indeed.


> **linuxonbute said:**
> I have a networked ( wireless ) Brother DCP585CW and have Ubuntu 10.04 on my laptop and 10.10 on my desktop PC. I went through the full set of instructions on the brother website and it works fine. One thing of note is that, on my laptop I did it in the order they said, but on the desktop I did it in a different order first time ( which didn't work ) then removed it all and did it again in the correct order and it then worked. This includes scanning as well, not just printing.

Is the printer a network printer or connected via USB?
i am puzzled as to how you can print 'simple' stuff but not photos and so on. 
Can you print text in colour or just black? 
Are you certain you downloaded the correct drivers? 
If it is networked are you sure you have a suitable network address for it, that you followed the instructions for a network printer and not the locally connected printer and that it is set up for the right paper size etc?

@gordintoronto

I was astonished too! I chose Brother as I thought the brand was Linux friendly, but I suppose not. So far during my four-ish years using Ubuntu, printer compatibility has been one of the most frustrating.

---

