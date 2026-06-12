---
title: "SCX-4200 Samsung and envelopes"
date: 2009-11-05
forum: Hardware
---

### Post by giocarra on 2009-11-05
SCX 4200 on ubuntu 8.04
 
Hoping to be in the right section of the forum!
I beg your pardon for my bad English.

Let me expose my problem :
last week I installed on a pc owned by my brother-in-law, Ubuntu Jaunty (09.04) and all gone fine.
He has a Samsung SCX4200 multifunction printer and all gone like a charm (Printer and also Scanner), but one thing : I'm not able to print an envelope, all kinds of envelopes.
When I try to print envelopes I receive this message (printed on the envelope itself) instead off the name of the sender and the name of the receiver :

Code:

"INTERNAL ERROR -uwaPaperSize[en_media][1] != (u16)(-1)
POSITION: 0x9b2575 (10167669)
SYSTEM :  : H6FW/xl_tbl
LINE :180
VERSION : QPDL 1.40 11-14-2005 "

I think this is an error due to software but the driver I installed is the last one (aug 2009) released from Samsung and, as I told before, printer and Scanner work very very fine.
Please note that with Windows Vista this does not succeed.
Does someone had my problem? And solved it?
I hope to receive from your courtesy a good suggestion about my problem.
Thanking in advance, best regards!

giocarra

---

### Post by metapaso on 2009-11-07
Hi,

I also have an SCX-4200. I also had trouble printing envelopes on Hardy, Intrepid, and Jaunty. I don't remember receiving your same error message, but I had a lot of bad printing, including error messages.

I have upgraded to Karmic (9.10).  I am using openoffice.org 3.1.1 and the most recent Samsung linux driver. (From Jan 2009).

My envelope printing is working now (I have to do some manual adjustments of the margins in OpenOffice, but no errors).

When I updated the Samsung Linux driver, I first uninstalled the old Samsung linux driver, rebooted my computer, and installed the new one.

When I upgraded to Karmic, I made sure to keep a copy of my old /etc/cups/cupsd.conf file and my /etc/sand.d/dll.conf file. The dll.conf file has the word "smfp" on the final line.

(During the upgrade process, the update manager asks if I want to replace some configuration files with newer versions.  I make a copy of the file in my own ~/backups/karmicupdate folder so that if something doesn't work, I can compare the new configuration file with my old version. Then I click "Replace").

What program are you using to print envelopes? Have you tried changing your paper size configuration?

Damon

p.s. Your English is great! Careful with the word "succeed", it's a false cognate for "succedere". You're looking for the word "to happen".

---

### Post by giocarra on 2009-11-08
Hi metapaso,
thank you very much for your kind reply.
The PC I'm writing of is owned by my brother-in-law and I'll see it to morrow or the day after tomorrow.
I'll try to use your suggestion hoping it goes fine.
I use Open Office Writer 
Also thanks for your appreciation of my "not so bad" English and for the suggestion about " to happen" and " To succees" .
I am aware of that difference, but in that moment I was confused;)

Thanks again and have a good week.
giocarra

P.S. I am not sure about what You did with your file /etyc/cups/cupsd   and the file /sand...... Did you use your backupped ones or the KK ones?

I've been advised against the upgrade from JJ to KK. People on the Italian Forum says it is better to install KK from the CD

---

