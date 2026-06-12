---
title: "printer recognized but not printing"
date: 2012-02-20
forum: Hardware
---

### Post by goodtimes200 on 2012-02-20
Hi All,

I am running Kubuntu 11.10 and have a canon mg5220. Whenever I start a print job, the printer display fires up and shows that the print job is being processed so there is definetly communication with the printer. However, the job dies rather quickly. I have scoured the logs and all I see is the following error in auth.log:

Feb 20 17:37:29 glacier dbus[1125]: [system] Rejected send message, 1 matched rules; type="method_call", sender=":1.434" (uid=7 pid=3588 comm="home 12 user  PDF Test Page 1 noCollate finishi") interface="org.freedesktop.ColorManager" member="FindDeviceById" error name="(unset)" requested_reply="0" destination="org.freedesktop.ColorManager" (uid=102 pid=8549 comm="/usr/lib/x86_64-linux-gnu/colord/colord ")

Perhaps it is some user/group permission problem but I cannot figure it out. Any help is very much appreciated.

---

### Post by beesblaas on 2012-07-28
I had the same kind of problem. The printer menu said "processing" but it never printed.
The correct drivers were installed and the printer was recognised.
It is now fixed.

In my case I was using Ubuntu 10.04.
I installed a Brother printer (HL-3045CN) for a USB connection.
I downloaded the Brother divers from here:
[http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html](http://welcome.solutions.brother.com/bsc/public_s/id/linux/en/instruction_prn1a.html)

I installed two Debian driver files for my printer in this order: install LPR file, then install CUPS file
(First installing CUPS will give: "Error: Dependency is not satisfiable")
Install by simply double-clicking on the files - Ubuntu does the rest.

I also changed the permissions for the printer filter file, for Brother it is a file starting with "br":
/usr/lib/cups/filter$ sudo chmod 555 br*

After any such changes you have to restart CUPS: sudo /etc/init.d/cups restart

You can check your installion of the printer by typing this in your browser:
[http://localhost:631/printers](http://localhost:631/printers)

It still did not work. Print jobs were "processing" but not printing.

I also got the following error:
Print self-test page,  CUPS server error, There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

I finally got it working as follows:
In the web browser go to your installed printer, follow menu
Administration > Modify Printer
My printer was listed, (twice I think), in one entry it also mentioned the word USB, so I selected that. Then it printed !!

I'm not sure how all of this ties together but I hope it helps someone.
It is fantastic of Brother to provide Linux drivers. Many printer manufacturers cannot be bothered.

---

### Post by Kreaninw on 2012-07-28
Not much technical here in my case. I'm using Canon MP680. Do not download Canon driver from its website, it will not work. Just uninstall that driver(if you're already installed it) and plug in printer USB cable to Ubuntu, let Ubuntu find driver, done. :D

---

