---
title: "&quot;The system printing service doesn't seem to be available&quot;"
date: 2013-08-28
forum: Hardware
---

### Post by rickenboxter on 2013-08-28
Hi. I was printing happily for a long time, and then after an update I get "Sorry! The system printing service doesn't seem to be available" when I run "Printers"

I found one thread about this, which suggested to remove and reinstall everything associated with cups:[URL="http://ubuntuforums.org/showthread.php?t=1870429"]
http://ubuntuforums.org/showthread.php?t=1870429[/URL]

I tried 
sudo apt-get purge cups hplip 

and then
sudo apt-get install cups hplip

but no change. I tried rummaging around and deleting various config files, also unhelpful.



I took a look at the [DebuggingPrintingProblems webpage]("https://wiki.ubuntu.com/DebuggingPrintingProblems") but none of those instructions seem relevant and/or I can't execute them for one reason or another. 

I tried lpstat -r, it says "scheduler is not running," even after apparently successfully running sudo start cups

I tried to follow the instructions under "CUPS error_log", but they rely on cupsctl, which tells me:

cupsctl: Unable to connect to server: Transport endpoint is not connected

Unfortunately things started going wrong a month ago and I've been doing work-arounds since then. So I don't remember all the details of what might have triggered this problem.

I'm running 13.04 on a Lenovo X1 Carbon.

Thanks!

---

