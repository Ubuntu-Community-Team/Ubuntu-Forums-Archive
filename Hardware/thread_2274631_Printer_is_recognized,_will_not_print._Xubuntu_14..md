---
title: "Printer is recognized, will not print. Xubuntu 14.10."
date: 2015-04-21
forum: Hardware
---

### Post by bob120 on 2015-04-21
New to Xubuntu, very hard to find the correct info. This printer connects by USB , wireless cannot be trusted in my location.
Printers-localhost shows Brother-MFC-J475DW and Brother-J475DW(2), do I need to uninstall one of these?
If I select SERVER, I get "connect to CUPS server", do that then nothing.
Hit the printer(2) and I get print page that is rapidly flashing, print does not arrive at printer screen.
Then pick the first printer (above), hit "add", it goes to "new hardware" window, Device section highlights "enter URI". A box to the right wants "enter device URI". (What is URI?)
If I assume URI is URL, then my printer setup screen lists IP 0000.000.000.00 (zero's may not be the correct config.), just indicating there isn't one.
What am I doing wrong? I'm a senior, I can follow names / words found in pop-ups, I do not understand developer phrases. 
I don't see my printer listed in various pages. Did see one similar post (USB) that got moved to "developer", search the same phrase (the title) in "developer", no results. Considered date search, but lost the reference, only recall Sept, 2014.
Can this be solved? Should I reinstall Xubuntu with a partition for a windows OS that will run my printer factory disc?

---

### Post by gordintoronto on 2015-04-21
Yes, you should delete one of the printers. "Add" will add it again, so don't do that. And avoid "server," you don't have one.

In printers, if you click on the printer, then right-click and select "properties," you should see a window which includes "Print Test Page" at the bottom-right. If you click it, what happens?

I have a Brother laser, and it works well with all of the many versions of Linux I have tried over the past few years.

If you edit a document in Abiword and select "print," the printer should appear as an option, perhaps the default. Can you print the document?

---

### Post by pdc on 2015-04-21
so to set up a printer there are generally 3 steps:

1) establish a connection
2) install the drivers
3) register the printer on one's system

If I was advising someone how to install the drivers for the Brother MFC-J475DW, I would suggest they use the driver install tool that **_Brother offer from here_** [http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfcj475dw_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadend.aspx?c=au&lang=en&prod=mfcj475dw_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625)

an install script such as Brother and Canon offer; does both steps 2) and 3) whilst one sips a cup of tea. If one clicks to download and SAVE the Brother [COLOR="#0000FF"]driver install tool[/COLOR] ............ then if one opens a terminal and copies the commands below:

and pastes in the following commands into the terminal ......... hit enter after each paste .............

```
cd Downloads
```

```
gunzip linux-brprinter-installer-2.0.0-1.gz
```

```
sudo bash linux-brprinter-installer-2.0.0-1 MFC-J475DW
```

so the final command will fire up the installer; ask you a couple of questions; and hopefully all will go well ................ that creates a printer registration that you should be able to see on [http://localhost:631/printers/](http://localhost:631/printers/) so if you identify the [COLOR="#0000FF"]**queue name**[/COLOR] that the install created; and it works; you can delete the others that don't .............

---

### Post by bob120 on 2015-04-22
Hi Gord, Thanks for your response, we are neighbors, Niagara Falls.

The test page does nothing. Confident now that this model is not supported.
I haven't tried Abiword yet, back later on this. First I'll delete the second one.
 I got desperate for printing 2 days ago over income tax filing. Worked around it by phoning, snail mailed my return(s) late yesterday. 
Pdc's post below has a code method. I'm clueless on the correct terms to speak in too!

Thank you pdc for your patient description on this procedure. Appears straight forward enough. I'll try this later today, minus distractions. Back soon with results.

I sure enjoy Xubuntu, able to set a decent contrast and font size for failing eyes.

pdc, I just tried your solution, failed, checked the terminal info and the second command line failed. How do I correct that line? 
I used upper case were shown in lines 1 & 3, is upper case needed in Linux?
I am very pleased on your method of help, just what new uses need.

I have loaded another computer with Xubuntu 14.10, attempted printer install on this one.
I ungraded to Xubuntu 15 something on this older HP, 2 gb, 200 gb. web pages like news sites are a little slower, only have 100mbs DLS internet connection.

I just tried to install on the HP computer  that is running Xubuntu 15.xx. The command lines worked, answered Y to all the prompts.
Second to last says "Will you specify the device URI [y/n]", answered Y, I did not read, just yes to all.
Next line says " select the number of destination Device URI. ->{ ". 
What is this? How do I find? Is that last line correct, (did I erase 2 clicks accidentally switching between unfamiliar windows?) Should I start over and NOT specify the Device URI ?

---

### Post by pdc on 2015-04-26
Hi Bob;

I learn something new each day; going back over Brother's instructions (I did a fresh download for myself of that file to see the instructions), [http://support.brother.com/g/b/downloadhowto.aspx?c=au&lang=en&prod=mfcj475dw_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625](http://support.brother.com/g/b/downloadhowto.aspx?c=au&lang=en&prod=mfcj475dw_us_as&os=128&dlid=dlf006893_000&flang=4&type3=625)

..........and I now see they say .......................

> When you see the message "Will you specify the DeviceURI ?",

 **For USB Users: Choose N(No)**
 For Network Users: Choose Y(Yes) and DeviceURI.

The install process may take some time. Please wait until it is complete.

so if you click on this link [http://localhost:631/printers/](http://localhost:631/printers/) tell us how many separate lines of Brother printer are listed in the left hand column called Queue Name .............(I am just wondering if the install script finished its job and did a registration and so will that registration work to print for you?)

__________

if it doesn't work, can you delete it...............run the install script again.................say NO when asked about the device URI...............and see if you get a successful registration......................................

---

### Post by bob120 on 2015-04-26
I have 2 printers listed, "generic text-only printer" and "Brother MFC-J475DW CUPS", both are listed as "idle", both attempts are USB.

Yep I hit Y, instead of N.

I got both deleted, now retry, restart.

pdc, Yes it works! I am grateful for this help.

I'll redo 14.10 on the Acer, I will upgrade to 15, figure out check sum too.

I am real impressed with the logon for this site.

Thanks to the hosts.

---

### Post by pdc on 2015-04-27
> Yes it works! 

.............well done.............Bob.............you're a champ! Enjoy

---

### Post by bob120 on 2015-05-06
I am not able to repeat Brother install on a disc copy reinstall of Xubuntu 15.04. Tried more than 3 times. Failed with this and 14.10.
This time I disconnected internet before installing. Results in language errors, a popup box long gone.
I'm getting other issues while attempting Thunderbird (that is not the topic).

---

### Post by pdc on 2015-05-06
hi bob; sorry to hear of your latest troubles: ............so 14.10 was working ............and you have put 15.04 on .............and it is not so far going well ..........

_____________

Can I suggest you have a look at this link [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS) as the little hidden secret is that every two years an LTS version comes out for ubuntu .......... supported for five years .......... so once running, it should be good for 5 yrs..... so the last little treasure was 14.04 so if anything............I would have suggested you go backwards to 14.04 as that would see you good till 2019!! 

Have a close look at the chart: the support time for the standard release of ubuntu is getting short: 15.04 will only be good till Feb next year; 14.04 is good till April 2019 ....................... 

________

so you just sequentially pasted in the commands that are in post #3 of this thread ............ ??

what does ```
/usr/sbin/lpinfo -v
``` give in a terminal please .............. with the printer plugged in and turned on ......... ?

---

### Post by bob120 on 2015-05-07
Success again! Took awhile as all worked fine until I hit "test print" without the printer USB connected, then the Terminal started with adding more software, wanting further commands.

I had to cancel, retry, failed. So delete the installer downloader from downloads, get it again from the Brother link, reenter the above posted instructions in Terminal and it worked.

If anyone else references this topic, you need the Brother installer package FRESH each attempt, even though it is there, (asks to overwrite Y/N?) Y. Then it works.

---

### Post by bob120 on 2015-05-07
pdc, 
Thanks for helping out again. I selected Xubuntu 14.xx as it was rated as user friendly for folks with low computer skills. Then it wants to upgrade, results in 15.xx. The 14.10 disc does not work well, scrapping it.

Until I figure out how to backup by disc I'll just reload 15.04. This is often due to responses from Kijiji ads, wanting to infect computers. I'm looking for sandbox options that is not complicated. First I got to get my Gmail / 15.04 working together, Thunderbird fails due to Gmail blocking, thats a different thread.

I'm not sure what thread it was but a poster suggested I should contact Linux user groups to find a factory disc (or pure from someone skilled in verifying) locally. I'll do that.

---

### Post by bob120 on 2015-08-20
Since my last post I quit Xubuntu and went to Windows 7 on a different computer. Problem was the unsecure Gmail option (Thunderbird)  for placing Kijiji ads with photos. Since then I found I can change my email acct on Kijiji, using a different email provider. Other computer is now infected from ad responses. I never have repair discs anymore, cdrom and dvdrom never function regardless of MS instructions. Always fallback to an old win7 and this damaged Xubuntu, reinstall, update for a day or so.

I have reinstalled this version of Xubuntu, updated and attempting to install Brother printer MFC-J475DW, same as this thread refers to.

Downloaded the installer package from Brother, the link provided by pdc, then entered the commands in the same pdc reply. All works until the last command is answered N for the UBS cable operation. Then  more "response" happens and expects me to enter a command. I tried twice, Y, N, password and  "enter", no result. I see my printer, has 2 tests in quene, will not print them as more info is wanted by the install???

I copied that to downloads, any suggestions?

---

### Post by bob120 on 2015-08-20
CANCEL my request from 4 minutes ago. I have plugged the USB cable into the wrong computer.
 		 			 				:oops:

---

### Post by bob120 on 2015-08-20
Dumb as it gets. Printer works for test page. 

While I'm on site I'll update my post on bypassing ink level sensors.

Then continue with Xubuntu setup for my needs.

---

