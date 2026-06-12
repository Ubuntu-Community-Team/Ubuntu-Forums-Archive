---
title: "Email client that can delete individual messages from POP server"
date: 2008-11-09
forum: General Help
---

### Post by ctalbertma on 2008-11-09
I would like to use an e-mail client in Ubuntu that can delete individual mail messages from a POP server. I have found none that can do this. Can someone point me to such a program?

---

### Post by mlissner on 2008-11-09
My bet is that mutt can. I don't know mutt, but that sounds up its alley.

---

### Post by ctalbertma on 2008-11-09
Perhaps a GUI client would be preferred to a text-based one. Any suggestion on one that can delete individual messages from POP? Thanks.

---

### Post by scouser73 on 2008-11-10
I think Thunderbird can delete messages via POP3.

---

### Post by ctalbertma on 2008-11-10
I think I tried, Evolution, Thunderbird, and Eudora 8. All GUI I have tried allowed me to delete messages, but it's either all or nothing. Keep all of them on server, or keep none of them there.

I don't seem to be able to delete message 17, but keep message 16 and 18 (I have a habit of deleting messages on the prime number 
scale...).

Any suggestion? Advice?

---

### Post by ellgor on 2008-11-10
Hi,

Take a look at Kmail, its got more functions than I'll ever use, in your case, check out the "configure pop filters" section, hope this of use.

Regards, Ellgor

---

### Post by HermanAB on 2008-11-10
They all can do that.

You have to tell the client to 'keep' messages on the server, since it will download and delete by default.  Then, once you configured it so that it won't delete by default, you can delete individual messages.

'Hope that helps!

Herman

---

### Post by ctalbertma on 2008-11-10
I am afraid I don't understand. I just tried again. In Evolution, I set the messages to be left on POP server after Evolution has retrieved it. 

so I have just received a message, and I have it already on the machine. There seems to be no way for me to delete that message which still resides in the POP server. I tried deleting it in Evolution. Use a web mail program and the same message is still there. Use another e-mail program to check the same account, it is still there. Evolution allows messages to be deleted after say N days. I simply would like to get rid of the message that is on the POP server after Evolution has downloaded it. No option for me to do so.

Can there be more specific instructions? Maybe just telling me that it can be done isn't quite useful to me. Or maybe just tell me I am missing something, some command or codes somewhere. Let me know the exact procedures for deleting a message that resides in a POP server. thanks.

---

### Post by mlissner on 2008-11-10
This doesn't answer your question, but you know about IMAP right? It's another protocol for mail retrieval that is better than POP3 in just about every way.

---

### Post by Frogbarf on 2008-11-22
Install the Windows client "Pegasus" under Wine, then use its "selective mail download" feature. Mark the message for deletion only and click "make it so."

Because of bugs in Wine, Pegasus will close unexpectedly, but just restart it and when you do selective mail download again, you'll see that the message you wanted to delete is, indeed, deleted. The bug is that when Pegasus auto-closes the selective mail download window, Wine misinterprets the action as "close program", not "close window".

I've tried many email clients in my day and have stuck with Pegasus through thick and thin. No other client has this feature so neatly implemented. Unfortunately, the fine people who write Pegasus have no plans to port it to Linux, so you have to make do with the Windows version and the concomitant screwy behavior of Wine.

---

### Post by TeXtonyx on 2008-11-22
"I simply would like to get rid of the message that is on the POP 
server after Evolution has downloaded it. No option for me to do so."

I will present what I think is the best solution first
if you don't like Thunderbird:

----------------------------------------------------

[http://sourceforge.net/projects/deletefrompop3/](http://sourceforge.net/projects/deletefrompop3/) 
# New release 0.5 available.    2008-11-05 

"Two Perl scripts for deleting of selected messages left 
on the POP3 server. You can select messages for deleting 
from within your mail client missing this feature, like 
KMail and Evolution, then execute the script which actually 
deletes the messages." 

[http://deletefrompop3.sourceforge.net/](http://deletefrompop3.sourceforge.net/)
"Unfortunately my favourite mail client (Kmail) cannot leave 
messages on the POP3 server while retrieving them and delete them 
later, eg. when they are moved to 'Trash" folder (like Thunderbird)." 
[don't forget to compact the trash]

----------------------------------

Since Outlook Express does this as part of its programming, it
stands to reason that these perl scripts could be incorporated
into Kmail or Evolution to give them the same functionality as OE.
These scripts were written by somebody who had your problem. 

-------------------------------------------------------------


Thunderbird, under Server Settings for your account, the default is
to delete messages on the server after you have downloaded them.
Messages that you then delete on your computer are gone.

If you have more than one computer so that you want to download
the same messages some or all of those computers, then under
Server Settings, you can check the box which says, leave messages
on the server, and then check another box, 'until I delete them'. 

If you want to delete individual messages, then you go to the server,
if you choose to keep them on the server.  

Outlook Express does perhaps what you want:

   1. Open Outlook Express
   2. Select Tools/Accounts.
   3. Click on the Mail tab, highlight YourAccount and click on the Properties button.
   4. Click on the Advanced tab.
   5. In the Delivery section, select the checkbox to Leave of copy of messages on server.
   6. Select the appropriate checkbox to delete the messages from the 
server after a certain number of days or until the messages are deleted 
from the Deleted Items in Outlook Express.

So to delete individual messages, you delete it in Outlook Express
and then a final delete from the Deleted Items storage account.
When you log on to the email server the next time, they sync.
I don't suppose you could try using virtualbox or wine to run OE :(

A gmail account has a huge amount of storage and works for Linux.
You can leave the messages on the server which is helpful when
your computer fails and one hasn't made a backup.

---

### Post by tealio on 2008-11-22
Someone already mentioned it, but it seems like what you'll want is to use the IMAP protocol rather than POP3... POP3 usually downloads and deletes, or downloads and leaves on the server.  As far as i know, that's the only two options fo POP3...

IMAP basically syncs your local inbox with the server inbox.  When you delete an email locally, it deletes from the server.  anything you keep in your local inbox stays on the server...

IMAP really shines if you're going to be checking your email from 2 locations (work and home, as so many typically do)... Lets say you received 2 emails while you were at work... and you delete one, but decide, say to answer other from home later.  When you check your email from your home, you'll never see the one you deleted again, but the one you kept in your inbox is still right where you left it... this differs from POP3 in that either they would both still be there (server keeps msgs after download) or neither of them would (server deletes)...

hope this helps!

---

### Post by TeXtonyx on 2008-11-23
> **tealio said:**
> Someone already mentioned it, but it seems like what you'll want is to use the IMAP protocol rather than POP3... POP3 usually downloads and deletes, or downloads and leaves on the server.  As far as i know, that's the only two options fo POP3...

this differs from POP3 in that either they would both still be there (server keeps msgs after download) or neither of them would (server deletes)...   hope this helps!

When you delete email from Thunderbird with Account Settings -> 
Server Settings under the account name with the boxes ticked to 
"Leave messages on server" and then "Until I delete them" after
one deletes a message and opens and closes Thunderbird the message
will delete on the server. If you have the webpage for emails
open then that also has to be reloaded to see the results. 

What you can't do is have two different behaviors; delete locally
some messages and they stay on the server and delete other messages
and they are also removed from the server. Are you saying that
Imap can accomplish this "what you can't do with pop3"? 

tealio wrote:
"IMAP really shines if you're going to be checking your email 
from 2 locations (work and home, as so many typically do)... 
Lets say you received 2 emails while you were at work... and 
you delete one, but decide, say to answer other from home later. 
When you check your email from your home, you'll never see the 
one you deleted again, but the one you kept in your inbox is 
still right where you left it..." 

That sounds just like Pop if you check "Leave messages on Server"
and also (both) "Until I delete them"? It works like OE except
the description in OE is clearer, 

6. Select the appropriate checkbox to delete the messages from the 
server after a certain number of days or until the messages are 
deleted from the Deleted Items in Outlook Express. 

Thunderbird and OE have the same behavior, but TB doesn't make it
clear 'or until messages are removed to Trash in Thunderbird'.
I have the similar to home/office objective with two computers
which dual boot, so 4 email accounts that I want all the emails
to arrive at. I have a few accounts under the general account 
and I can change the settings between 'leave messages on server' or 
'delete messages after downloading', depending on which sub-account.

The OP was mistaken when he said Thunderbird didn't work like OE,
but I think he was right about Kmail and Evolution.

---

### Post by TeXtonyx on 2008-11-23
> **ctalbertma said:**
> I would like to use an e-mail client in Ubuntu that can delete individual mail messages from a POP server. I have found none that can do this. Can someone point me to such a program?

When you delete email from Thunderbird with Account Settings ->
Server Settings under the account name with the boxes ticked to
"Leave messages on server" and then "Until I delete them" after
one deletes a message and opens and closes Thunderbird the message
will delete on the server. If you have the webpage for emails
open then that also has to be reloaded to see the results. 

Or you can leave all the messages on the server. Take a particular
email message with the subject: Hi from Bro 
There is no global setting that will let you either delete 
"hi from bro" from the server and keep it on the server at the
same time, that is with a local choice for each particular email.

One can delete all the messages from server after downloading them locally, or
delete none of the messages after downloading them from the server (global)
or one can delete locally and delete from the server, the same message.
But with one particular message you can't sometimes delete the message
from the TB inbox and keep it on the server, Or, have the choice of
deleting from the TB inbox and remove it from the server... not at the
same moment. You'd have to change the global setting back and forth.
So you can delete all messages on the server that you downloaded, or
none of the messages on the server that you downloaded, or delete 
emails from TB and it will then delete the same emails from the server.

But any of these three behavior methods work for all the emails, one
can't use one method for a particular email, another method for a
different particular email, and a third method for another different
particular email. Not in the same session. You can switch between the
methods in your global settings between sessions. But not have all 3 methods 
available concurrently in the same session. Just one method at a time. 
With backups and moving email to another folder, you have some flexibility.

You can leave all the messages on the server, after you delete
them locally, just check "leave messages on server". Or delete
all messages on the server after you download them. Or leave
all the messages on the server except the ones you delete locally.
You can put all messages you want to keep in a folder named Keep
after moving them from the Inbox. Then you can delete all or some
of the messages from the Inbox and it will sync deletions with
the server if you have tick leave messages on the server and
the box under it, until I delete them. You can do an email backup
(labeled by the date) of messages you want to keep, and delete all in
the Inbox which can be set to sync with the server, so all are gone.
Later, you can restore your backup if you change your mind.
Windows has Mozbackup. Ubuntu has a manual method for TB,
[http://ubuntuland.nireblog.com/post/2008/02/12/how-do-i-backup-thunderbird-mail-and-profile-under-linux](http://ubuntuland.nireblog.com/post/2008/02/12/how-do-i-backup-thunderbird-mail-and-profile-under-linux) 

[http://www.customsoftwareconsult.com/phpBB2/viewtopic.php?p=2569](http://www.customsoftwareconsult.com/phpBB2/viewtopic.php?p=2569)
FEBE will backup Firefox and Thunderbird (and more) but you need
to customize it the first time. It's not as easy as Mozbackup.

---

### Post by ctalbertma on 2008-11-25
Thanks for all the information and replies. 

A few clarifications. I have been using Eudora as a mail client in Windows (for years). Eudora does allow individual message deletion from server, on POP, iMAP. It's a very convenient option when I have multiple computers and would want to get rid of (unwanted) messages which would otherwise be downloaded later in other machines. I don't quite see a lot of benefit of using iMAP given this feature in Eudora.

I can still run Eudora for Windows on a virtual box, so can work around.

It would be nice if I don't have to get onto virtual box unless I have to (or even wine). 

Somehow I can't import my Eudora address book to Evolution or Thunderbird, which is really a big, huge, critical minus...K-mail can somehow import my Eudora address book. But it seems K-mail can't provide the individual message deletion feature. I tried the suggestion above on script deletion on POP, but don't seem to get it to work (at least not yet).

thanks for all the suggestions, anyway.

---

### Post by TeXtonyx on 2008-11-25
"Somehow I can't import my Eudora address book to Evolution or 
Thunderbird, which is really a big, huge, critical minus.. "

TeX: When I have problems with using programs, I use google to
look up the answer by doing a search; the search terms that I used
were " how import address book thunderbird "
and the second entry down on the first page reported this,

[http://www.css.qmul.ac.uk/mail/thunderbird/import.html](http://www.css.qmul.ac.uk/mail/thunderbird/import.html)
From Eudora, Outlook or Outlook Express

"If you previously used Eudora, Outlook or Outlook Express to read 
and send email, you can easily import both locally stored mail and 
your address book into Thunderbird: "

Steps with pictures follow. Thunderbird can leave all the messages
on the server, remove all the messages on the server after a local
download, or lets you choose individual deletion of messages. TB
can import email and address books from Eudora. I know that because
I read the directions. Reading the directions is an important step
to learn on the road to becoming an expert. People who rely on their
imagined computer expertise are dooming themselves to remain computer
illiterates. Export your Eudora settings to Thundebird in Windows.
Thunderbird stores email information in a profile and content of 
those files is compatible with Linux Thunderbird. 

---------------------------

[http://www.freeemailtutorials.com/mozillaThunderbird/backupRestore.cwd](http://www.freeemailtutorials.com/mozillaThunderbird/backupRestore.cwd)

"While this Thunderbird tutorial focuses on Windows, please note that 
Thunderbird is a "cross-platform" email client: it runs and operates 
the same way on Windows, Apple's Mac OS X and Linux. 

Overview: this free tutorial shows you how to backup and restore your 
Mozilla Thunderbird emails, contacts (address books), and profile using 
MozBackup, which is freeware for Windows, and *manually*." ...

Manually:
"To back up the folder in which all your profile information is stored, 
go up three levels, so that you end up in the Profiles folder, of which 
Mail is a sub-directory. The Profiles directory contains a folder called 
[blank].default, (where [blank] is an unpredictable string of 
alpha-numerical characters.)"

"To restore your emails or profile manually, simply copy the folder you 
backed up into your profile folder. To restore emails only, copy the 
backed up email folder back into your Thunderbird Profile folder's 
subfolder which contains the Mail directory mentioned above."

So your goal is to take the Windows backup profile and replace the
newly created profile on the Linux Thunderbird.

C:\Documents and Settings\UserName\Application Data\Thunderbird\Profiles\xxxxxxxx.default\Mail 

/home/username/.mozilla-thunderbird/xxxxxxxx.default/Mail 

Those paths are close to accurate.
So you can mount the Windows partition and copy and paste
the correct content from Windows email folders to Linux email.

[http://fosswire.com/2008/03/04/migrate-your-thunderbird-emails-from-windows-to-linux/](http://fosswire.com/2008/03/04/migrate-your-thunderbird-emails-from-windows-to-linux/)

This has similar steps except for how to make profile.ini which I omitted.

---

### Post by ctalbertma on 2008-11-25
Dear TeXtonyx,

there really is no reason to be so presumptuous....

Been there, done that. It didn't work for my particular Eudora address file. I did use Thunderbird to "import" my particular Eudora address book file, and it made a mess out of it. There is no reason to try to figure out why it didn't work. 

Thanks for the note anyway.

---

### Post by TeXtonyx on 2008-11-26
> **ctalbertma said:**
> 
Been there, done that. It didn't work for my particular Eudora address file. I did use Thunderbird to "import" my particular Eudora address book file, and it made a mess out of it. There is no reason to try to figure out why it didn't work. 
----------------------------------

[http://blogs.chron.com/techblog/archives/2007/09/eudora_lives.html](http://blogs.chron.com/techblog/archives/2007/09/eudora_lives.html)

"Eudora, the venerable e-mail client that was discontinued last year by Qualcomm, is back from the dead and ready to party, this time as an open-source application being developed by the Mozilla Foundation.

Dubbed the Penelope Project, it's an effort to create a version 
of Eudora that's based on Mozilla's popular Thunderbird e-mail 
software. The first beta of Eudora 8.0 is now available for 
Windows and Macintosh computers. 

I downloaded the Windows version and, except for the setup 
process taking a very long time to export settings and e-mail 
from an older version of Eudora, I've been pleased with the 
experience. The software retains the basic look and feel of 
Eudora, but it's been updated and given a cleaner, more modern 
interface. It's completely free." 

-------------------------------------

[https://wiki.mozilla.org/Eudora_Releases#Eudora_8.0.0b4](https://wiki.mozilla.org/Eudora_Releases#Eudora_8.0.0b4)

 Eudora 8.0.0b4

The latest beta release of Eudora, version 8.0.0b4 (which includes the Penelope extension version 0.5a1) is now available for download. Use the links below to download. Please see the README for information on how to submit bug reports and new feature requests.

    * Windows installer
    * Mac disk image
    * Linux tar file 

--------------------------------------------
TeX:
Eudora 8 is now being developed under the auspices of mozilla,
which strive for cross-platform compatibility like Thunderbird.

The first webpage says that the Windows Eudora 8 imported email
settings from an older version of Eudora, albeit slowly.

I'm sure it's a priority for email settings to be imported or
migrated from the Windows version Eudora 8 and the Linux version 8. 
The directory structures should be quite compatible. At beta
stage some goals work and some don't and they lose capabilities
from one beta release to another. Perhaps you'll be able to use
a Linux version of Eudora itself when it reaches maturity. 

--------------------------------------------

[http://kb.mozillazine.org/Importing_and_exporting_your_mail](http://kb.mozillazine.org/Importing_and_exporting_your_mail)
written for Thunderbird

"If you have problems importing .EML files using the 
ImportExportTools extension try using eml2mbx to convert the 
.EML files to a mbox file and then import the mbox file using 
the ImportExportTools extension. A Google search will find 
several eml to mbox conversion programs. Whats unusual about 
this one is that provides a lot of control over how it converts 
the .EML files using a "eml2mbx.ini" file. 

If your old email client supports exporting the address book as 
either a .CSV or .LDIF file you can import it using Tools -> 
Import -> Address books -> Text Files. If not you might be able 
to use a program like Dawn to convert the address book to a .CSV 
file and then import it."

---------------------------------------

footnote: I just downloaded Windows Eudora 8 and it automatically
imported my email and settings from Thunderbird. Surprise. A step
in the right direction. I'm going to try it on Ubuntu next, see if
it imports email settings. Then uninstall Thunderbird and then
reinstall it and see if it can import settings from Linux Eudora 8.

---

### Post by TeXtonyx on 2008-11-26
"Somehow I can't import my Eudora address book to Evolution or Thunderbird, 
which is really a big, huge, critical minus..."

You can import your address book from classical eudora to eudora 8 in Windows.
Then export in ldif format from eudora 8, put in possibley C:\transfers
Tools -> Address Book -> Tools -> Export (choose ldif format, filename.ldif)

Boot Ubuntu and one can import filename.ldif from either Linux Eudora 8 or
Thunderbird. ~$ sudo  /usr/local/eudora/eudora 

Tools -> import -> Address Books -> LDIF (text file) -> 66.5GB Media (your
Windows partition) -> transfers -> EudoraWinAdBk.ldif (select it) -> open
success message: imported address book EudoraWinAdBk
Finish

I captured Eudora with the Address Book open within Ubuntu (attached)

---

