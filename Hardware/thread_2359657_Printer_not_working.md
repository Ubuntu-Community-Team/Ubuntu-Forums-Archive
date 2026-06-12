---
title: "Printer not working"
date: 2017-04-26
forum: Hardware
---

### Post by christon74 on 2017-04-26
Hello fellow-ubunters :)
I have a Canon MG 3150 (printer) which once was installed. I have no idea what quirk of fate uninstalled it. It is connected to a HP dc 7700. The OS is Ubuntu 16.04 LTS. When I click on the printer icon (system), a window opens and displays this message: "Sorry, the system printing service does not seem to be available". I have just opened a terminal screen and have typed the command: 
systemctl status cups.service
 
And here is the result:

christophe@hp1:~$ sudo su
[sudo] password for christophe: 
root@hp1:/home/christophe# systemctl status cups.service
Warning: cups.service changed on disk. Run 'systemctl daemon-reload' to reload u
&#9679; cups.service
   Loaded: masked (/dev/null; bad)
   Active: inactive (dead)
lines 1-4/4 (END)


I have suppressed several packages which were absolutely useless on this computer
but now I have absolutely no idea what I must do to reinstall this printer.
Printers-localhost says:
"printer service not available, start the service on this computer or connect
to another server" and then "CUPS server error, there was an error during the CUPS
operation; failed to connect to server"

All of this is very, very frustrating! :frown:

Again, thanks in advance for help and any piece of advice.

---

### Post by slickymaster on 2017-04-26
Moved to a thread of its own.

Please don't hijack other people's threads. Not only it dilutes community effort but it's also the wrong way to get the proper and adequate help to your problem.

---

### Post by kesetyan on 2017-04-26
Hi Christon74,

I see your post has been moved from the thread I started re: my printer problem.  As my problem is now marked as 'Solved' you may not have got any possible solutions there so you are better off in this new thread.

The solution to my problem (in Xubuntu) was simply to reinstall CUPS.  I didn't even uninstall it first so, if it was corrupted, reinstalling it over the top of itself still worked in my case.  Make sure your printer is 'off' if you try this, then, after the reinstallation of CUPS completes, switch it on and see if it is recognised.  

By the way, at the start of my problem my printer was listed in 'Printers' but showed an exclamation mark rather than a green tick.  As I couldn't find a way around that, I removed the printer from 'Printers'.  Check 'Printers' in your Ubuntu and see if your Canon MG 3150 is listed and if it is, whether or not it has a green tick or an exclamation mark. If the latter, then removing the printer from 'Printers' is probably a good idea before reinstalling CUPS.

I'm no expert and have only been using Xubuntu for a short while but I thought it worth sharing my experience.  No doubt you will get replies from more experienced forum members who will help you if my suggestion does not help in your case.

Good luck.

---

### Post by christon74 on 2017-04-26
Hi Slickymaster. Sorry, I did not mean to upset anybody and as a form of apology, I would like to say I have not read the full book about Ubuntu forum etiquette. I thought it was a good idea to post a message similar or relevant to somebody else's printing problem, and Kesetyan's thread read just that to me. As for getting satisfactory answers and solutions that work, I never fail to mark my own thread solved.
Good day to you.

---

### Post by christon74 on 2017-04-26
Hello Kesetyan:) _ Thank you ever so much for this tip and your mild mannered answer. I have just turn off the printer to reinstall CUPS. I keep fingers crossed and hope this does the trick. I then try my best to find where my thread has been moved.... and mark it solved, else some admin might well throw me out with a mop.:tongue:

---

### Post by christon74 on 2017-04-26
Hello again  :)
My Canon printer is now installed. One slight annoying thing though: it will only print the first ten or twelve lines of the document and then stops printing leaving 3/4 of the page completely blank....

---

### Post by ajgreeny on 2017-04-26
I think in that case you had better remove the SOLVED tag by going to **Thread Tools** at the top of the thread.

---

### Post by pdc on 2017-04-26
Hi christon74

"it will only print the first ten or twelve lines of the document and then stops printing leaving 3/4 of the page completely blank...."

If you go into your PRINTERS folder, and right-click on the icon for your MG3150, select PROPERTIES and look in the DEVICE URI and the MAKE & MODEL section: perhaps you paste the results back here; 

sometimes the Model set up may not be exactly what your printer is: one can change it by clicking on the CHANGE button; that opens the database; if you select Canon, it may offer variants; it is likely have the open-source Gutenprint installed; 

_______________

you can also install the drivers that Canon supply to you in a debian format from here [http://support-asia.canon-asia.com/contents/ASIA/EN/0100393702.html](http://support-asia.canon-asia.com/contents/ASIA/EN/0100393702.html) and it comes down as cnijfilter-mg3100series-3.60-1-deb.tar.gz .. if you SAVE it as it is downloaded, the commands to install are
cd Downloads
tar -zxvf cnijfilter-mg3100series-3.60-1-deb.tar.gz
cd cnijfilter-mg3100series-3.60-1-deb
sudo ./install.sh

---

### Post by kesetyan on 2017-04-28
Hi Christon 74,

Many potential forum members who might be able to help you will not view your thread as it is still marked 'Solved' - you can edit this by going to your first post, click the 'Edit' button and choose 'Advanced' - you should then be able to remove 'Solved'.

Good luck.

---

