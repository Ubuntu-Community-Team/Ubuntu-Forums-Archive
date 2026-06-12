---
title: "Thunderbird segfaulting upon selecting folders"
date: 2008-11-19
forum: General Help
---

### Post by tseligkas on 2008-11-19
Hello everyone,

I have upgraded Hardy Heron (8.04) Ubuntu to Intrepid Ibex (8.10) and the upgrade went fine. I am faced with an issue which most likely has nothing to do with the upgrade, however I don't tend to accept coincidences easily ;)

I am using Thunderbird (now in version 2.0.0.17) for a long time without any problems, having thousands of emails in it, applying filters, having my Inbox containing many subfolders and using an archiving method for emails older than half a year.

Now Thunderbird still works and my emails seem to be intact, however after a few actions involving selection (point and click) of folders (say going from Inbox to Sent items then to an Inbox subfolder and Inbox again) the Thunderbird window just closes. I can compose emails, open address book, etc. but when I return to the main window and "play" the above scenario I get the aforementioned behaviour. Opening Thunderbird from a terminal only gives me a Segmentation fault message when the window closes.

I googled for similar posts but I couldn't find anything. I am about to try reinstallation in the way Tommy suggests in **[here]("http://ubuntuforums.org/showpost.php?p=1101987&postcount=7")** (for a different problem), but I would like to know if anyone else here has seen anything similar or can anyone suggest a more elegant (less hassle) solution.

I'll be happy to provide any further information if needed.

Many thanks!

---

### Post by tseligkas on 2008-11-19
Not even a guess? :(

---

### Post by tseligkas on 2008-11-28
OK, I disabled the message pane (message preview). The situation seems to be a little improved, however a still get crashes, just not so frequent.

I am beginning to suspect that the Thunderbird mailbox is corrupted. Could anyone care to offer an advice how to fix this? I could follow a procedure (I'll google for it) of backing-up emails & filters and reinstalling Thunderbird but I don't know if this will de-corrupt the mailbox.

Any suggestions are welcome!

---

### Post by wil on 2009-07-08
I have the exact same problem with 9.04 using version 2.0.0.22 (20090608)

---

### Post by tseligkas on 2009-07-09
> **wil said:**
> I have the exact same problem with 9.04 using version 2.0.0.22 (20090608)

I have upgraded ubuntu and Thunderbird and have the same versions as you now. The problem is persistent and I haven't yet found a solution...

---

### Post by tseligkas on 2009-07-15
I found a more "stable" way to replicate the problem.

I have created a rule to move emails older than half a year from one set of folders to another set of backup folders. The operation is complete and I proceed into compacting the former folders. When being inside (having selected an email from) one folder and compacting the other and moving to the compacted folder we get Thunderbird crashing.

Let's take a scenario: 2 folders -> "Job" & "Friendly Spam". I have selected the folder "Job" and I right click -> Compact the folder "Friendly Spam". When selecting the folder "Friendly Spam" Thunderbird segfaults. One extra parameter that may make things differ in behaviour is that no email has been previously selected in the folder "Friendly Spam" upon selection of the folder. It may not crash if otherwise.

---

### Post by wil on 2009-07-23
I am unable to reproduce this bug on my wife's computer so I think it must be some corruption in the profile.

The only problem is I do not want to loose all my saved emails!!!

---

### Post by wil on 2009-08-22
still not solved in version 2.0.0.23 (20090817)

---

