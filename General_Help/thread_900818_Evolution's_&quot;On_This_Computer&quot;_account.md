---
title: "Evolution's &quot;On This Computer&quot; account"
date: 2008-08-25
forum: General Help
---

### Post by atorch on 2008-08-25
Hi,

I have the exact same question as this guy:  [http://ubuntuforums.org/archive/index.php/t-746992.html](http://ubuntuforums.org/archive/index.php/t-746992.html)

Evolution lists two accounts:  "On This Computer" and "myaddress@university.edu."

The Sent folder under "On This Computer" contains all the emails I've sent using evolution.  The Inbox under "On This Computer" is empty, with the exception of a single "Welcome to Evolution!" message.

The Inbox under "myaddress@university.edu" contains all the emails I've ever received.  The Sent folder under "myaddress@university.edu" is empty.

How to I tell evolution to either...

1 - move the "On This Computer" Outbox to "myadress@university.edu" and remove "On This Computer" (from Evolution's sidepanel)

-or-

2 - move the "myadress@university.edu" Inbox to "On This Computer" and remove "myadress@university.edu" (from Evolution's sidepanel)

Basically I want to collapse "On This Computer" and "myaddress@unveristy.edu" into one.  It's redundant to have both.

---

### Post by MoLE on 2008-09-01
One method I would try would be to delete your current account information, then recreate it, but make sure you have the "make this my default account" option ticked in the account settings.

---

### Post by atorch on 2008-09-02
> **MoLE said:**
> One method I would try would be to delete your current account information, then recreate it, but make sure you have the "make this my default account" option ticked in the account settings.

My only issue with this is that, under edit -> preferences, my account is already listed as "name@place.edu [Default]."  So isn't it already the default account?

---

### Post by plucky on 2008-09-02
> Evolution lists two accounts: "On This Computer" and "myaddress@university.edu."

Isn't **myaddress@university.edu** not just a sub folder of the "On This Computer" folder? Evolution won't let you delete the default folders.

Check what Message Filters have been set up for your **myaddress@university.edu** account. **Edit > Message Filters**

If you remove all the filters,then your mail should then use the default Inbox and Sent mail boxes.The Outbox is only temporary storage for mail that hasn't yet been sent.


Good Luck

---

### Post by schpet on 2008-11-07
> **atorch said:**
> 
Basically I want to collapse "On This Computer" and "myaddress@unveristy.edu" into one.  It's redundant to have both.

I want to accomplish the same thing with my gmail account but have had no success, it was set up as the default account and there are no filters. The "On This Computer" account is completely empty.

---

### Post by atorch on 2008-11-09
> **schpet said:**
> I want to accomplish the same thing with my gmail account but have had no success, it was set up as the default account and there are no filters. The "On This Computer" account is completely empty.

Same here, I just reformatted and installed 8.10, followed evolution's setup wizard, checked the "make this my default account" box, did not create any filters... and the "on this computer" account is empty, save one "welcome to evolution" message.

---

### Post by mkantor1 on 2008-12-21
I have the same issue.  I'm using Gmail with IMAP (what about you guys?).  

Here's a screen capture:

[IMG]http://mattkantor.com/misc/mail_folders.jpg[/IMG]

---

### Post by dcstar on 2008-12-22
> **atorch said:**
> 
.........
Basically I want to collapse "On This Computer" and "myaddress@unveristy.edu" into one.  It's redundant to have both.

Evolution needs the default folders to function, and if you have a separate IMAP account then that cannot replace the default folders, so it is not "redundant" because you can delete that IMAP account at any time.

IMAP file structures are an addition to your Evolution system, not a replacement for them because Evolution has no control over them because they are on a separate e-mail system.

---

### Post by zorkerz on 2009-03-15
Well that sucks. I decided to give evolution a try today after using gmail through a browser for a few years. Im having a hard time finding reasons to keep using evolution. If im right using pop3 would sidestep the issue discussed here but I still want to access my mail online fairly often. 

The 'on this computer' section does not bother me terribly because it can be collapsed. What is irking me even more at this point is the organization on all the files under my gmail account. There is inbox, junk, trash, then also my gmail lables (bugs, fb, friends, lists, mcgill, ubuf, uvm) and a [Gmail] folder that contains all mail, drafts, sent mail, spam, starred, and trash. To make it worse it appears that these can only be organized alphabetically. Thats 16 separate folders only a  few of which I use often.

 Does this bother other people and if so what have you done about it? 

Can anyone propose some reasons why I might want to continue using evolution instead of gmail from a browser?

Sorry I woke up an old post with a bit of a rant.

---

### Post by EmanueleBardelli on 2009-05-11
try this:
cd $HOME/.evolution/mail/
rm -r local (before this, be sure there aren't emails inside!!!)
ln -s /dev/null local

the result is a unexpandable "on this computer"...


Emanuele

---

### Post by cheeserolls on 2009-05-30
Zorkerz, it bothers me too.  It drives me mad.

I tried Emanuele's solution, but found that Evolution completely failed to start.  Deleting the link to /dev/null makes it work again, but only because it recreates the big ugly pointless local folders for me.

It's annoying, because the software's aimed at desktop users, and how many of them will actually send and receive mail locally?  Very few.

---

### Post by R1kARD0 on 2009-07-24
it bothers me too. But well Evolution has a better integration with gnome so... i use evolution.
But someday if the local folder isn't removed i will swithing to thunderbird :/

---

### Post by mnml on 2009-10-29
> **EmanueleBardelli said:**
> try this:
cd $HOME/.evolution/mail/
rm -r local (before this, be sure there aren't emails inside!!!)
ln -s /dev/null local

the result is a unexpandable "on this computer"...


Emanuele

Quite good workaround, the "Ont This Computer" title remains but the subfolders are gone ;-)

---

### Post by mr_steve on 2009-10-29
> **atorch said:**
> Hi,

I have the exact same question as this guy:  [http://ubuntuforums.org/archive/index.php/t-746992.html](http://ubuntuforums.org/archive/index.php/t-746992.html)

Evolution lists two accounts:  "On This Computer" and "myaddress@university.edu."

The Sent folder under "On This Computer" contains all the emails I've sent using evolution.  The Inbox under "On This Computer" is empty, with the exception of a single "Welcome to Evolution!" message.

The Inbox under "myaddress@university.edu" contains all the emails I've ever received.  The Sent folder under "myaddress@university.edu" is empty.

How to I tell evolution to either...

1 - move the "On This Computer" Outbox to "myadress@university.edu" and remove "On This Computer" (from Evolution's sidepanel)

-or-

2 - move the "myadress@university.edu" Inbox to "On This Computer" and remove "myadress@university.edu" (from Evolution's sidepanel)

Basically I want to collapse "On This Computer" and "myaddress@unveristy.edu" into one.  It's redundant to have both.

I can sort-of halfway solve this for you. You can't get rid of the "On This Computer" folder structure, but you can have Evolution save your sent mails into your "myaddress@university.edu" Sent Mail folder.

Open Edit->Preferences. Select your mail account and click 'Edit'. On the 'Defaults' tab, click the button next to 'Sent Messages Folder:' and select the folder you'd like sent messages to be stored in.

Otherwise, if you really want your university mail to go to the "On This Computer" inbox, and to not have the extra "myaddress@university.edu" folders, you need to see if you can set your mail account up as a POP account, rather than IMAP.

Hope this helps.

---

### Post by DanneUK on 2009-12-07
Thank you mr_steve!  That has been bugging me for ages, but I just got round to having time to fix it. :D

---

### Post by dicedan on 2010-06-10
> **EmanueleBardelli said:**
> try this:
cd $HOME/.evolution/mail/
rm -r local (before this, be sure there aren't emails inside!!!)
ln -s /dev/null local

the result is a unexpandable "on this computer"...


Emanuele

I tried this, but now I can no longer send e-mails. Does anyone know how to reverse it. I'm not very good when it comes to terminal commands.

---

### Post by dcstar on 2010-06-12
> **dicedan said:**
> I tried this, but now I can no longer send e-mails. Does anyone know how to reverse it. I'm not very good when it comes to terminal commands.

```
mv .evolution .evolution.org
```

Start Evolution so it creates a fresh .evolution folder.

It is crazy to try and hack a program in this way to try and get around **what it is designed to do** just because of a quibble over the screen.

Having "On This Computer" collapsed just takes up one solitary line, why whinge about that?

---

### Post by dicedan on 2010-07-27
Thanks dcstar, sorry for the long time to say thanks, forgot I had even asked the question.

---

### Post by Jonners59 on 2010-07-28
Interesting arguments below reading this thread!

Personally I like the folders and the ability to create folder structures - though I too do not use the "On this computer".  I use gmail and my own domain for which google host, so have the same tagging method of listing/filing eMails - personally I hate it.  there is a limit to the size or should I say length of tag so when that translates to a file system it is not very flexible and robust, and certainly not scalable.  I have 3 accounts on one machine and associated structures...  I guess because I use mine for business and hence large number of complex conversations I need to filter, with normal personal use, it's not so important.

This is not an Evolution limitation.  I have tried many clients, my fab is - sorry guys - Outlook 2007 & 2010, but they do not work on Linux with SSL/IMAP, even using WINE, Crossover although there is a workaround using sTunnle, but it is not supported and nobody helps if it does not work.  Outlook uses *.pst databases for each account, so once the new accounts are set up, and the default is changed, after reboot the default account can be removed, hence they get away with the issue you guys are having with Evolution.

PS.  To change the alphabetical order you can add either a space or number in front of the file name..... And you can put folders in folders creating a structure, which may help, that's what I do a lot of.  But, yes, putting them in the order you want without the need for games would be a nice to have.

One thing you may be able to answer for me, though....  When I delete stuff in Evolution I assume it deletes it on the google server...  However, what I have noticed when I go in via web browser that my Google All Mail they are still there - What happens if I delete everything from Google All mail, will I loose everything else?

Horses for courses.

---

### Post by jacob.david on 2010-10-29
I don't have any solutions to get rid of "On this computer" which annoys me too. But you can keep the sent items in the same mail account instead of "On this computer". Open the preferences and the mail account. click Edit and choose the Defaults tab and set the "Sent Messages Folder" to the folder of your choice.

---

### Post by Jonners59 on 2010-10-29
> **jacob.david said:**
> I don't have any solutions to get rid of "On this computer" which annoys me too. But you can keep the sent items in the same mail account instead of "On this computer". Open the preferences and the mail account. click Edit and choose the Defaults tab and set the "Sent Messages Folder" to the folder of your choice.

Yes, since the thread, which is quite old now, I have learnt a bit more and use the accounts settings differently.  Still think it is like a Outlook 2003.  OL 2007 and 10 are far ahead.  Never mind.

And as for gmail...  about time they allowed better filling.  Have such a limit to the folder structure is frankly "crap".

---

### Post by West201 on 2011-01-12
Has anybody found a solution to this annoying folder ? 

Please post the solution on here when someone does :)

In the mean while I'll subscribe to this thread.

---

### Post by alawson on 2011-01-21
Echo jessej above!
This is really annoying. All my mail is help in IMAP folders. I neither want nor need the local folders. Same with calendar. Both mail and calendar are accessed from multiple clients on multiple platforms - why would I want to keep mail on a PC in my house when I'm on the road with my 3g laptop, or at the office with my phone?

Additionally, this PC (running 10.10) keeps losing the default account setting and hiding my IMAP folder structure. Grrr.

---

### Post by mulbric3 on 2011-08-28
Same here.

Thing is: I seriously don't get how the developers thought that anyone would like this weird interface with an additional 'On my computer' segment. Most of its content remain empty anyway...

---

### Post by drknot on 2011-09-06
I've finally managed to get the Sent onto the IMAP homeserver (FSG3).  What I need is to ge tthe outgoing filters to work  I want to match all outgoing mail and copy it to the local folder  Tried Sender contains * - fails Tried Size > 0 -fails  anyone got these working.  Personally I rely on local copies so have no issue with the structure, but need help to get the sent to work as I want - self duplicating locally and IMAP home server.  FWIW, the homeserver fetches by POP3 to create local IMAP mailbox

---

### Post by Baz00 on 2012-12-01
Removing the "On this computer" folder is now possible.


[LIST]
[*] Go to menu: Edit >> Preferences >> Mail Account
[*] On the left column next to the account name, make sure "Enable" is not ticked.
[/LIST]
 
:KS

---

### Post by wildmanne39 on 2012-12-01
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

