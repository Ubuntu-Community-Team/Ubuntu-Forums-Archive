---
title: "Brother MFC-J425W installed; no longer prints"
date: 2013-01-04
forum: Hardware
---

### Post by Catlike on 2013-01-04
Hello. 
I am using Ubuntu 12.04. 
I am not knowledgeable about computers. 

I installed the Brother printer MFC-J425W many months ago and it worked fine until about 6 weeks ago. I guess after downloading & installing one of many recommended updates, it quit printing and scanning.

When I send a document to the printer, the printer's display shows "Receiving data". The little dots flash as per usual, then the display goes back to resting mode. The print queue briefly shows the document name and "Processing", then goes blank. Nothing prints out. Paper and ink supplies are fine.

I followed instructions from another thread 
([http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother](http://ubuntuforums.org/showthread.php?t=1999216&highlight=brother)) 
and re-installed the driver. My printer shows up as connected. There is now also a new printer name: "DCP 110C". I have no printer by this designation. 

After re-installing the driver, the results are precisely the same as I reported above: "Receiving data" on the printer's display; print queue *briefly* shows the document name and "Processing"; then all is blank, and nothing prints out. This is the case whether I select "MFC J425W" to print to, or the new, anomalous "DCP 110C" printer.

Can you provide me with very beginner-friendly trouble-shooting tips? Beginner-friendly for me means that instead of saying "Check your whumpdown files" please show me exactly *how* to check my whumpdown files. I do not know command lines at all. 

I also need the directions for trouble-shooting the scan function with this printer. Perhaps that comes later?...

Thank you.

---

### Post by kurt18947 on 2013-01-04
I don't have access to a 12.04 Unity install right now.   Are you connected via USB or a network connection?  When I've had a similar problem in the past, it was due to an flaky network printing protocol.  I don't recall how to check that on Unity.  I usually install a older  printer management package still available in the repositories that gives me more information and options.  

Re the 'new' printer, My suspicion is that you installed the wrong driver.   Isn't DCP-110C the first printer on the list of many?  I would probably just remove the DCP-110C.  I'll find a machine with Unity later and check back on this thread.

Edit:  Ubuntu (unity) does use the 'old' printer management app.  You can open the 'printing' app, right-click the MFC-J425W icon, left-click 'properties' and see if there's anything amiss there.  I've also had Brother printers become 'paused' for no apparent reason - there'll be two vertical bars over the printer icon - or be disabled.

---

### Post by Catlike on 2013-01-05
Hey kurt18947 - 

Thanks. I did the Printer Properties and got to the Settings page. I saw that the "Description" and "Device URI" have what looks to be correct (MFC J425W). However, the "Make and Model" field showed "Brother DCP-110C CUPS v1.1". So I selected "Change" next to "Make and Model" field. This opened a couple windows -- one small "searching for drivers" windowlette and a larger "Change driver" window. 
After a brief search, the search window disappeared and the Choose driver window remained. I chose "Brother" from a list of printer brand names, clicked a "Forward" button at lower right, and got a list of Brother printers. I found and selected "MFC-J425W CUPS" from the list, and then again clicked the "Forward" button at lower right of the window. 
The next window was "Existing settings". It offered 2 choices: (1) Use the new PPD as is; (2) try to copy the option settings from the old PPD. The 2nd choice was pre-selected, so I clicked "Apply" at the lower right. 
I closed all windows, opened a document, and printed. It worked just fine. 
Thank you again for helping me.

P.S. How do I change the thread title to read "Solved"?

---

### Post by kurt18947 on 2013-01-05
Good Job!  To mark the thread solved, look at the beginning of the thread, top of the screen.  You should see "Thread Tools".  Click that and you should find what you need.

---

