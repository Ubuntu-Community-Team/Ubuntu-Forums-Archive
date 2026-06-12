---
title: "Partial Upgrade breaks cups-pdf"
date: 2009-03-21
forum: Installation &amp; Upgrades
---

### Post by slumbergod on 2009-03-21
I've been using Xubuntu for over a year now and been very happy. For the first time I was prompted to do a Partial Upgrade and assuming it was part of the normal upgrade cycle I let it do its business.

I remember seeing something to do with cups-pdf in there (synaptic's history seems to have not recorded any of the changes made with this partial upgrade so I can't confirm what it did). 

Afterwards I thought I would try printing a pdf to see if it still worked given that updates often break things in Ubuntu. It failed.

I tried to fix it by completely removing and reinstalling all cups components. No luck. 

Then I tried manually creating the missing PDF folder in home. No luck.

I changed the permissions on the cups/backend folder. No luck.

It seems to print to pdf (i.e. the windows comes up and shows the pdf being generated) but no pdf appears in the PDF folder, nor anywhere else I can determine.

It is no big deal for me because I nearly always print-to-file so I can choose where the pdf is saved and this still works. But I thought I would post a warning so that anyone else that encounters a Partial Upgrade can think twice. 

Perhpas I will stop upgrading when prompted, or at least wait a day or two. It isn't really a big deal for me because I have a bit of experience with Linux and can usually fix issues but it does make me concerned that new users trying out Linux to escape m$ hell might be put off by this recurring problem.

If anyone else encountered this issue and found a resolution I would be grateful for the solution. I tried everything I could find in the forums without success.

PS: has anyone noticed how using google does a better job of search the ubuntu forum that the website's own (useless) search tool?

---

### Post by slumbergod on 2009-03-22
Ok, found a solution so hopefully if anyone else encounters this they can try this also.

I found a thread which mentioned something about cups-pdf being removed in intrepid because it was "obsolete". I recall that was indeed part of the message I got from the partial upgrade.

Reinstalling cups-pdf did not fix it. I still had to make a new PDF folder in my home directory. Credit to Piraja whose posting gave me the correct commands to fix the permissions Print to PDF would work again.
[http://ubuntuforums.org/showpost.php?p=6000099&postcount=12]("http://ubuntuforums.org/showpost.php?p=6000099&postcount=12")

The commands from Piraja's post were:
cd /usr/lib/cups/backend
sudo chown root:root cups-pdf
sudo chmod 700 cups-pdf

---

