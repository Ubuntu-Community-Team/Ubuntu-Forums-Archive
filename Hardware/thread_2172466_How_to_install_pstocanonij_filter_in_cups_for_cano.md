---
title: "How to install pstocanonij filter in cups for canon printer (12.04 64 bit)?"
date: 2013-09-05
forum: Hardware
---

### Post by stu3 on 2013-09-05
I've been trying to install my Canon mp620 printer to my new laptop for a couple of days now without joy.
  I've tried every instruction I can find online and only one has come  close to working: it finds the wireless printer and installs the driver  (Canon MP620-630 BKIntegration Ver.4.0 Universal), but I get a message  in the printer status box that says:
  [INDENT]   Idle - File "/usr/lib/cups/filter/pstocanonij" not available: No such file or directory
 [/INDENT]  I've looked in the folder and that file is missing. I've found the  file on my old laptop (running 12.04 32bit and the same printer) but  because its a root permission only folder, I can't add it to the new  one.
  I don't know if adding it will solve the problem but can someone tell me how to do it?
  Cheers.
      
stu

---

### Post by pdc on 2013-09-07
Hi Stu;

I wonder if you are now using a 64bit system?

I suspect the drivers Canon packaged for the MP620 when it was released were only 32bit drivers; 

(similarly they are not releasing 128bit or 256bit drivers, as they are not being used now)

so your system may need some symbolic links to tell it to look elsewhere

try 

> [COLOR="#FF0000"]sudo ln -s /usr/lib /usr/lib64[/COLOR]

and

> [COLOR="#FF0000"]sudo ln -s /usr/local/lib /usr/local/lib64[/COLOR]

and then 

> [COLOR="#FF0000"]sudo service cups restart[/COLOR]

to restart cups .......

any joy?

______________________________________________

if you check in lib64, pstocanonij is likely to be there .........your system if 64bit is likely to be /usr/lib[COLOR="#0000FF"]**64**[/COLOR]/cups/filter/pstocanonij

whereas for 32bit mine is /usr/lib/cups/filter/pstocanonij

---

