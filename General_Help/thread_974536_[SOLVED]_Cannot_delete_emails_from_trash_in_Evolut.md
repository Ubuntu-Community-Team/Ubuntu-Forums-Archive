---
title: "[SOLVED] Cannot delete emails from trash in Evolution"
date: 2008-11-07
forum: General Help
---

### Post by Enigmatic on 2008-11-07
I'm not sure why, but any messages in the trash cannot be deleted. If I undelete them, they are removed from the trash and back to the original position. As soon as I put anything in the trash, it can't be deleted. It just sits there...the summary says it's storing the folder, it completes without errors but nothing is ever deleted.

Ideas?

---

### Post by Tamlynmac on 2008-11-07
Have you tried:
Evolution/file/empty trash

---

### Post by Enigmatic on 2008-11-07
Well yes, and it does nothing. No error messages either.

---

### Post by Tamlynmac on 2008-11-08
Have you tried highlighting the trash folder and evolution/folder/expunge?

See this site:
[http://www.go-evolution.org/FAQ](http://www.go-evolution.org/FAQ)

---

### Post by dcstar on 2008-11-08
> **Enigmatic said:**
> I'm not sure why, but any messages in the trash cannot be deleted. If I undelete them, they are removed from the trash and back to the original position. As soon as I put anything in the trash, it can't be deleted. It just sits there...the summary says it's storing the folder, it completes without errors but nothing is ever deleted.

Ideas?

Right-click the Trash folder and select "Empty Garbage bin".

---

### Post by Enigmatic on 2008-11-08
Ok, when doing an expunge I noticed that it gave me an error about folder/summary not matching for one of my folders. I delete the ev-summary for that folder, and any messages that were in that folder originally were then possible to delete.

It seems like the remaining messages in the trash are originally from my inbox. I removed the ev-summary for the inbox, but it doesn't empty the trash (with no error either, just says expunging 100% and finishes with no error, but the messages are still there).

This is using a POP3 account with mail stored on my PC.

---

### Post by Enigmatic on 2008-11-10
Anyone else have any ideas?

---

### Post by Divine Amoeba on 2008-11-10
I had been struggling this problem for a while now.  Pretty much figured out the solution myself.  I am using evolution 2.24.1 on intrepid.

Backup your evolution data using the "file->backup settings" option.
Go to your home folder.
Check the "show hidden files" in the view menu to see all the files.
Navigate to ".evolution/mail/local" folder.  select and DELETE all files with the following extensions:
.index
.ev-summary
.cmeta
Do NOT delete the files ending in ".data"
Restart evolution.  Give it a few minutes to load as it will have to re-create all the indices.
You should now be able to delete files from trash and junk.

Hope this helps.

Disclaimer: I am not responsible for any loss of information you may encounter or if your machine should spontaneously combust.

---

### Post by Enigmatic on 2008-11-10
Awesome, that did the trick. I had a feeling it could be solved with a similar method.

---

### Post by exploder on 2008-11-10
Divine Amoeba, this would be a nice edition to the known bugs and workarounds thread for Intrepid. Nice fix!

---

### Post by zbry on 2008-11-11
It did the trick in my case too. 
Exploder, I had the same problem in Hardy.

---

### Post by Aypok on 2008-11-12
I had a similar problem and this thread helped fix it (thanks, by the way), but I didn't need to do everything in Divine Amoeba's post; all I had to do was run the back-up portion and all was fixed for me.

So: If you have similar problems, try running the back-up bit first, then try deleting/expunging the emails again. If it still doesn't work, *then* try the rest of what he suggests in his post.

Hopefully that'll save some people a few minutes. :)

---

### Post by zbry on 2008-11-18
The problem has come back. Deleting the files doesn't work any more. The amount of deleted mail in the Trash is rising but I can't get rid of them.

---

### Post by Swagman on 2008-11-21
Worked for me... Will keep an eye on it though.

---

### Post by rpaco on 2008-11-26
Had the same problem, and the solution almost worked, however Evolution started up much quicker than usual and when I emptied the deleted items folder all but 4 were deleted.
I have added (deleted)  new items and these can be "emptied/expunged. but the original 4 still sit there. Expunging the folder has no effect at all on them
Will try deleting all those files again to see if that will work.

---

### Post by rpaco on 2008-11-26
Interesting, I tried Forwarding un-deletable messages in the deleted folder (the 4 I mentioned above and they have all disappeared!!! I guess this forced the index to be rebuilt.

---

### Post by rpaco on 2008-11-26
SORRY Duplicate post, wireless network playing up.
Interesting, I tried Forwarding un-deletable messages in the deleted folder (the 4 I mentioned above and they have all disappeared!!! I guess this forced the index to be rebuilt.

---

### Post by YuriBCN on 2009-01-08
SOLVED, but not permanently!
I followed the very useful instructions yeasterday, but when I rebooted this morning, same old same old!  :-/
I'll try again!

BTW, has this bug been reported?

Best. YuriBCN

---

### Post by yuriry on 2009-02-08
Thank you Divine Amoeba.  The fix initially did not work for me because of multiple accounts, but deleting the suggested files from all account-specific sub-folders solved the problem.  This is great, because I've been struggling with this for a while now.

```

#!/bin/bash
# see http://ubuntuforums.org/showthread.php?t=974536
cd $HOME/.evolution/mail
find -name "*.index" -exec rm {} \;
find -name "*.ev-summary" -exec rm {} \;
find -name "*.cmeta" -exec rm {} \;

```

---

### Post by Van Fanel on 2009-05-06
I also have this problem (Intrepid 64bit, Evolution 2.24.3)

To go around it, I only need to delete the file Inbox.ibex.index (in folder ~/.evolution/mail/local)

Unfortunately, every time I close and reopen Evolution, the problem resurges. To re-solve it, I have to go once again delete that &$%$# file.

There is some discussion here:
[https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/287811](https://bugs.launchpad.net/ubuntu/+source/evolution/+bug/287811)

and here:
[http://bugzilla.gnome.org/show_bug.cgi?id=550414](http://bugzilla.gnome.org/show_bug.cgi?id=550414)

---

### Post by chmac on 2009-05-09
I've had this problem also. I could not delete messages in *some* folders, not all, but some local folders. I found the solution was to delete the .index, .cmeta and .data folders as suggested *and* to delete the folder.db file in .evolution/mail/local.

I wanted to clear my entire inbox so I deleted all the Inbox files, the folder.db file and then restarted evolution. All the mail had disappeared. When I deleted only the Inbox files, the list of messages was still there, but I couldn't read the messages because the actual message had disappeared.

---

### Post by Ian Sinclair on 2009-06-01
Just doing the backup and restarting Evolution did it for me, without deleting and files.

---

### Post by paul_h on 2009-07-30
> **Divine Amoeba said:**
> I had been struggling this problem for a while now.  Pretty much figured out the solution myself.  I am using evolution 2.24.1 on intrepid.

Backup your evolution data using the "file->backup settings" option.
Go to your home folder.
Check the "show hidden files" in the view menu to see all the files.
Navigate to ".evolution/mail/local" folder.  select and DELETE all files with the following extensions:
.index
.ev-summary
.cmeta
Do NOT delete the files ending in ".data"
Restart evolution.  Give it a few minutes to load as it will have to re-create all the indices.
You should now be able to delete files from trash and junk.

Hope this helps.

Disclaimer: I am not responsible for any loss of information you may encounter or if your machine should spontaneously combust.

Backup and restart did not solve this problem for me but Divine Amoeba's solution above did work. I deleted ALL files ending in .index, .ev-summary and .cmeta in the /.evolution/local sub-directories and on re-starting Evolution was able to completely empty Trash.

Thanks Divine Amoeba. This problem was really bugging me.

Paul.

---

### Post by Cuba71 on 2009-09-11
Nothing works in my installation.

I even tried uninstalling Evolution and re-installing it, and all the messages came back.

This is really anoying, specially with a version that is suppossed to be stable

---

### Post by chmac on 2009-09-14
Backup your data, wipe out ~/.evolution/ and then restore. You'll definitely remove the messages when you wipe out that folder, just hope you can restore your data minus those messages.

---

### Post by nvdb on 2009-12-01
so has anybody already made a solution for this. The go-around is not solid and works only now and then

---

### Post by Morgonte on 2010-02-08
I've the very same problem, just that none of the workarounds actually work for me. I've deleted every file in .evolution/mail/local except *.data and the ones without extention. I've made a backup and restore. I've checked the file properties. Still when I try to empty the trash or expunge it I get a error telling me that my ~/.evolution/mail/local/inbox doesn't exist, which is nonsense.
All messages I delete goes to the trashbin and sits there eating up my system disc, and I simply can't get rid of them. I really love Evolution, but this bug will force me to move to another mail client if not fixed very soon.

---

### Post by billir on 2010-05-24
I might add that you can completely shut down evolution by going into 
System => Administration => System Monitor => Processes => Look for all things evolution and close them off.
I found it helped with the  removal of files as above.

---

### Post by chmac on 2010-05-24
> **billir said:**
> I might add that you can completely shut down evolution by going into 
System => Administration => System Monitor => Processes => Look for all things evolution and close them off.
I found it helped with the  removal of files as above.

Running `evolution --force-shutdown` will do this for you in a single command. Closing processes through system monitor will send them a kill signal while this command will let them shutdown gracefully.

---

### Post by Weekendpartier on 2010-07-17
**Evolution cannot delete trash because of file folder mismatch.**
After I deleted the cmeta files - Evolution works for one time and then
it's back to not emptying the trash.  The other commmand method works
too but then it's back to the error messages after one use.  I give up.

---

### Post by nrayever on 2010-08-21
> **Divine Amoeba said:**
> I had been struggling this problem for a while now.  Pretty much figured out the solution myself.  I am using evolution 2.24.1 on intrepid.

Backup your evolution data using the "file->backup settings" option.
Go to your home folder.
Check the "show hidden files" in the view menu to see all the files.
Navigate to ".evolution/mail/local" folder.  select and DELETE all files with the following extensions:
.index
.ev-summary
.cmeta
Do NOT delete the files ending in ".data"
Restart evolution.  Give it a few minutes to load as it will have to re-create all the indices.
You should now be able to delete files from trash and junk.

Hope this helps.

Disclaimer: I am not responsible for any loss of information you may encounter or if your machine should spontaneously combust.

The best solution, so far! Thanks a lot.

---

### Post by Denis Mahony on 2010-11-23
Re: Evolution 2.28.3

That solution did not work for me.

I eventually solved it by :
 selected Trash
select all messages
<left mouse button>
From menu ,
Select Undelete  ( **YES UNdelete**)

all messages weree deleted
It displayed:
'no messages in this folder'
Close Evolution
On reopening, Trash was empty

:D:D

Sounds like a toggle flag flipped the wrong way ?

Denis

---

### Post by Joliea on 2010-11-24
Mine's still not solved. There is a folder i created a while back and is under inbox. When trying to delete the folder it tells me 

"Cannot delete folder "Inbox/e".

Because "Folder 'Inbox/e' is not empty. Not deleted."."

Any help anyone?

---

### Post by Michl on 2010-11-24
This worked for me, too.  I skipped the backup and
for good measure went into the folder .evolution/mail/local/
#evolution.sbd and deleted Trash.cmeta 

M

---

### Post by Denis Mahony on 2010-11-24
Re Message #32.
Very embarassing ! 
Of course all it did was copy the messages back to the originating folder :redface:

I still has the issue for new deleteions ...Trash is still in trouble !

D.

---

### Post by leito1979ar on 2011-05-06
Same issue on Evolution 2.32.2 , ubuntu Natty 11.04. Any idea?

---

### Post by chmac on 2011-05-06
The folder structure has changed slightly on 11.04 or probably on Evolution 2.32. Anyway, the folders in question are now ~/.local/share/evolution/mail/local/ and so on. I think if you try the steps above but with that folder name, you'll get the same result as above.

---

### Post by fonsi2099 on 2011-05-28
That fine it works, with 11.04,

Thank you for the simple and efficient help.


:popcorn:

---

### Post by pme 72 on 2011-06-16
What seemed to work for me in Lucid 10.04 was:

The instructions in #31
Then the instructions in #32
Then going to Drafts where the undeleted files were, deleting them again
Then Empty Trash

On restarting Evolution the Drafts folder was empty and the Trash folder was empty.

Thank you

---

### Post by PrimeRadiant on 2011-06-28
Hi I'm having the same problem in that I cannot permanently delete emails in evolution (trying to delete all mail in the all mail folder under gmail). I followed the below advice and found the evolution folder in 

 ~/.local/share/evolution/mail/local/

I delete all the files ending with the appropriate extensions as per amoebas advice. I then restarted evolution and encountered the same problem with emails coming back. Does anyone have any idea what's going on? BTW I tried #31 and #32 but the only thing that happened was there was no number indicating the number of messages in my 'all mail' and 'inbox' folders. The messages that were in 'all mail' had come back.


> **Divine Amoeba said:**
> I had been struggling this problem for a while now.  Pretty much figured out the solution myself.  I am using evolution 2.24.1 on intrepid.

Backup your evolution data using the "file->backup settings" option.
Go to your home folder.
Check the "show hidden files" in the view menu to see all the files.
Navigate to ".evolution/mail/local" folder.  select and DELETE all files with the following extensions:
.index
.ev-summary
.cmeta
Do NOT delete the files ending in ".data"
Restart evolution.  Give it a few minutes to load as it will have to re-create all the indices.
You should now be able to delete files from trash and junk.

Hope this helps.

Disclaimer: I am not responsible for any loss of information you may encounter or if your machine should spontaneously combust.

---

### Post by clevertomato on 2011-07-19
The deleting of the *.index and *.cmeta files works for me, too, but this error happens all the time. I'm not going to do this workaround every time. How about someone actually fixing this software? What a pain. I'm getting really irritated having to hack, poke, and workaround so many things in Linux. We're talking about emptying trash, for crying out loud. How long has evolution been around? ... and it can't empty trash without some time-consuming terminal hoops to jump through every time? What's the deal?

---

### Post by chmac on 2011-07-19
I've only ever experienced this problem once or twice. Evolution, by and large, works just fine on my machine. More than that, for a piece of software that is free as in beer and free as in freedom, I'd say it does a damn good job. shawnboy, you can always ask for your money back. :-)

Free software is not always perfect, neither is unfree software. I think the developers of Evolution for the work they have done so far. I'm grateful for that. The beauty of free software is that you, shawnboy, like anyone else, are free to fix the bug that troubles you, free to hire somebody to fix it, or free to wait until somebody else chooses to fix it.

---

### Post by clevertomato on 2011-07-20
I can appreciate what your point, chmac, and have been on that side of the conversation before. The freedom thing wears thin after a while, though. I'm free to change engines in my car, or fix it myself when it breaks, but people don't buy cars so they can enjoy the freedom of working on them every other week. They buy them to get from point A to point B. You may point out that I used the word "buy." True. People pay for cars because the kind of car they could get for FREE would be a piece of crap that they would have to fix all the time. Exactly my point. Now, auto mechanics buy pieces of crap cars, but we're not all auto mechanics, now, are we? Neither are we all code monkeys that can manipulate C, C++, Python, etc. in our sleep.

Bottom line: I'm a big Linux fan. It has many pros. It also has many cons, and one is usability stuff like this. My Evolution does this every time I open it. On the one hand people wonder why Linux isn't on the majority of desktops. In the next breath, they're telling people to get stuffed or "fix it yourself." If a reliable email client WITH my freedom is asking too much, then one of them has to go.

... I have to use Windows to ...
properly and efficiently tag photos, print envelopes, read multipage tiff files, send/receive faxes, stream some videos with PMS because only Windows version has AVISynth, make zip files that are readable by Windows users... the list goes on and on. I'm such a big fan of Linux that I wish all these common things would be fixed so that I could get rid of Windows completely and for good.

Meanwhile, if anyone knows a fix for Evolution errors every time I try to expunge the trash, please let me know. I'm on Lucid with all latest updates.

---

### Post by mark bower on 2011-07-20
for what it's worth, i have used Mozilla Thunderbird for at least 4 years without significant problems, at least 3 years on Ubuntu, and currently on 10.10.  I started using Thunderbird on XP in preparation for moving to linux.  so, maybe give Thunderbird a try if you are really bugged by Evolution?

mark bower

---

### Post by chmac on 2011-07-20
@shawnboy, agreed, there are trade offs. I'd personally like to see a funding ecosystem that allowed users to put money behind bugs that particularly bug them. There are one or two niggles that I'd pay to see fixed. Anyway...

It sounds like something is out of whack on your system. I didn't get this problem every time on lucid. Have you considered updating? There are a couple of potentially bigger bugs in the latest evolution also...

Do you have the backports repo enabled? You might find a newer version of evolution in there.

---

### Post by clevertomato on 2011-07-20
After more searching and experimenting... I tried removing ~/.evolution/mail/local/folders.db then restarting Evolution. So far so good. I've started Evolution, emptied trash, deleted things, started, emptied, etc. several times now and it has worked so far. Woohoo.

Mark, I have thought about switching to Thunderbird for some time, but never have made the leap. Old habits I guess.

Chmac, your funding idea isn't bad. Maybe one of these days. Thanks for the tips. I'm on Lucid with all updates because I need reliability (LTS)... so that's why I haven't upgraded to a later release.  *grin* Hopefully this particular bug will remain behind me.

---

### Post by zero244 on 2011-07-20
Thanks for the tip Shawnboy.......the previous methods would not work for me.
Im using Evo 2.32, the version from Lucid

Deleting the folders.db file worked like a charm.

PS: I really like Evolution........its a nice piece of work overall. Im glad your tip worked because my trash folder was getting huge.

---

### Post by chmac on 2011-07-21
Happy days. Glad you got it working. :-)

---

### Post by JockeF on 2011-08-12
hey thanks!
Removing the folders.db file helped me with my "storing folders"-problem with Evolution on Ubuntu 10.10. I have 2GB:s of stuff in my mailboxes but now Evolution starts and stops in an instance again. I have suffered from really slow shutdowns for Evolution since I upgraded to 10.10, so this was really welcome. And now I managed to empty my trash as well, it was the trash of one account only that couldn't be emptied. It appears that the trash problem somehow was related to the slow storing of folders.
Joachim

---

### Post by zero244 on 2011-08-12
Deleting the folders.db file worked for me as well.
Plus Evolution had an update not long ago, which I installed. I haven't had any problems since.

---

### Post by thesios on 2012-04-28
Thanks for the tip; this worked wonders!

---

### Post by thesios on 2012-04-28
In fact, it fixed more than an inexpungible trash folder, it restored all of the messages I was bringing over from an old computer to this one (yeah, I don't have 50 posts, so I can't change my profile to show what version of Ubuntu I'm using and that I've moved from Lincoln City).

So...thanks again!

---

