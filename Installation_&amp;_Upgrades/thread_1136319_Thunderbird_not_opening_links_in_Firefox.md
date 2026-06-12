---
title: "Thunderbird not opening links in Firefox"
date: 2009-04-24
forum: Installation &amp; Upgrades
---

### Post by American on 2009-04-24
I've read every post on here about it. After upgrading from 8.10 to 9.04 and now having FF 3.0.9 and TB 2.0.0.21 I just can't make it work.

Made sure FF was the default browser.

I edited the preferences in TB's config file and added:

user_pref("network.protocol-handler.app.http", "/usr/bin/firefox-3.0");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox-3.0");

then even tried

user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");

neither worked.

I'm stuck and getting tired of copy/pasting links all day.

Any help would be appreciated.

---

### Post by halovivek on 2009-04-25
check the correct version of the firefox and change it.
just firefox 3.0 will not do more.

---

### Post by American on 2009-04-25
Yeah but in /usr/bin there is only

firefox
firefox-3.0


That's your choices...and firefox is a symlink to firefox-3.0 which is a symlink to:

firefox-3.0: symbolic link to `../lib/firefox-3.0.9/firefox.sh'

Which is: /usr/lib/firefox-3.0.9/firefox.sh

I even tried that in the config file but of course it didn't work.

---

### Post by caro on 2009-04-25
I made all the same edits you did and no luck here either.  I did check Evolution and hyperlinks worked there, so my guess is it is a problem with Thunderbird.  I've not had any updates from the bugs I filed with launchpad or upstream in a couple of days.

---

### Post by novosirj on 2009-04-25
I have the same problem. Has anyone filed a bug yet (and/or figured out what to file one against)? It's not the /etc/alternatives configuration as it has been in the past. Clicking a link does nothing at all.

---

### Post by caro on 2009-04-26
I filed a bug in launchpad and upstream.  

[https://bugs.launchpad.net/ubuntu/+source/mozilla-thunderbird/+bug/363577]("https://bugs.launchpad.net/ubuntu/+source/mozilla-thunderbird/+bug/363577")

[https://bugzilla.mozilla.org/show_bug.cgi?id=489080]("https://bugzilla.mozilla.org/show_bug.cgi?id=489080")

---

### Post by simonhk on 2009-04-26
For information, I did have this problem on 8.10, and still do on 9.04.

It is very annoying, as are the other problems that I had in 8.10 (and still in 9.04) such as the inability to resize the preview pane and the loss of the status line at the bottom of the Thunderbird window showing status when connecting to download e-mail.

---

### Post by American on 2009-04-26
Well... I guess we'll just wait and see what happens.

Thanks for filing the bug report.

---

### Post by mltriebe on 2009-05-01
Anybody fix this yet?  I did a clean install on my wifes computer and that is the only problem she has mentioned so far.  I should add I do not have this problem with my computer.  Both are running Jaunty.

Thanks, Mike

---

### Post by American on 2009-05-01
It's quite an annoying problem... having to copy links out of emails which I have to do ALOT with my job...but I'll live.

Oh well...someone will figure it out soon, I have faith.

---

### Post by American on 2009-05-04
Anyone seen any updates on this?

---

### Post by caro on 2009-05-05
No updates yet.  The last questions/suggestions the developers asked me were if thunderbird-gnome-support and firefox-gnome-support were installed and if I had my preferred applications set.  (The answer to all were "yes").  So, they seem to be working on it but nothing so far.

---

### Post by American on 2009-05-13
Any updates?

---

### Post by mltriebe on 2009-05-15
Here is what finally worked for me and I hope I can finally help out somebody else in the forum.  You will need to be able to see hidden folders in your User Folder to see the .mozilla-thunderbird folder.

I added the following lines to the bottom of the home/Your User Name/.mozilla-thunderbird/random code.default(In my case jxdcdjud.default)/prefs.js

user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.ftp", "/usr/bin/firefox");

and then save the file.  I was able to edit the file with a text editor with no problems and you should just be able to cut and paste the code from here.

Hope this helps, Mike

---

### Post by simonhk on 2009-05-15
Thanks Mike, that has fixed the problem of non-working hyperlinks for me.

Simon.

---

### Post by frniek on 2009-05-17
Sorry Mike, but these lines were allready in the prefs.js file. The about:config in the advanced preference tab did that for me. So I still assume that the problem is not with Mozilla, but in Ubuntu 9.04.

Greets, Niek

---

### Post by m3asmi on 2009-05-17
hi 
I have the same problem in my system 
I can't open the link & I can't do update 
this is the message :
	
An insoluble problem appeared during the initialization of data packets.

Please report this error as a bug in the package "update-manager 'and include the following error message:

'E: Encountered a section with no Package: header E: Problem with MergeList / var / lib / dpkg / status, E: The package lists or file "status" can not be analyzed or read. "

---

### Post by American on 2009-05-18
This already exists in my prefs.js file:

user_pref("network.protocol-handler.app.http", "/usr/lib/firefox-3.0.9/firefox.sh");
user_pref("network.protocol-handler.app.https", "/usr/lib/firefox-3.0.9/firefox.sh");

Still no worky...

---

### Post by caro on 2009-05-19
Still no love here either.  No updates in over a week from the bug I filed.

---

### Post by nexxus07 on 2009-05-26
I have the same issue on Kubuntu howver I realized that if Klipper is running (clip board application in KDE) and I rightclick and "copy Link Location" I get a popup in the right top corner which allows me to open the link in my browser. 
Still hoping for a real fix in Jaunty.

---

### Post by American on 2009-05-29
Any love on this issue?

---

### Post by presence1960 on 2009-05-30
I recall having the same issue in Hardy. I removed TB and reinstalled and it worked fine. Not saying that will work for you as no one seems to know exactly what the problem is. But it's worth a try.

---

### Post by American on 2009-06-11
Surely this deserves some attention...pretty basic function.

---

### Post by American on 2009-06-24
Come on guys...this is no small quirk, pretty basic function that needs resolving.

---

### Post by designzinthesun on 2009-07-04
This works...

System -> Preferences -> Preferred Applications
Now, for the Web Browser click "Open link in new window"
Then, close.

Links open right up in Firefox from Thunderbird emails.

---

### Post by American on 2009-07-04
> **designzinthesun said:**
> This works...

System -> Preferences -> Preferred Applications
Now, for the Web Browser click "Open link in new window"
Then, close.

Links open right up in Firefox from Thunderbird emails.

Nope...still nada.

---

### Post by designzinthesun on 2009-07-04
I just started a new user and and set Thunderbird up on that one and it opens up links without having to change any settings.

---

### Post by American on 2009-07-06
> **designzinthesun said:**
> I just started a new user and and set Thunderbird up on that one and it opens up links without having to change any settings.

A new user in Ubuntu or Tbird?

---

### Post by presence1960 on 2009-07-06
> **American said:**
> A new user in Ubuntu or Tbird?

create a new user in thunderbird - open a terminal and run ```
thunderbird -profile manager
```

Back up your bookmarks to html file first, then run that command. Don't delete the old profile until the new one is created. You don't have to delete the old profile if you don't want to. Then restart thunderbird by exiting profilemanager and starting tbird. and import bookmarks.

P.S. Thunderbird must not be opened to run profilemanager.

---

### Post by American on 2009-07-09
***Bookmarks*** in ***Thunderbird***?

and...

thunderbird -profile manager isn't doing a thing for me...neither is firefox -profile manager

even tried sudo thunderbird -profile manager .... nada.

---

### Post by presence1960 on 2009-07-09
> **American said:**
> ***Bookmarks*** in ***Thunderbird***?

and...

thunderbird -profile manager isn't doing a thing for me...neither is firefox -profile manager

even tried sudo thunderbird -profile manager .... nada.

that's because there is no space between the words profile and manager. This is the command ```
thunderbird -profilemanager
```
sorry about the typo.

---

### Post by American on 2009-07-09
> **presence1960 said:**
> create a new user in thunderbird - open a terminal and run ```
thunderbird -profile manager
```

Back up your bookmarks to html file first, then run that command. Don't delete the old profile until the new one is created. You don't have to delete the old profile if you don't want to. Then restart thunderbird by exiting profilemanager and starting tbird. and import bookmarks.

P.S. Thunderbird must not be opened to run profilemanager.

> **presence1960 said:**
> that's because there is no space between the words profile and manager. This is the command ```
thunderbird -profilemanager
```
sorry about the typo.


You're not making any sense to me...

I'm creating a new profile for THUNDERBIRD...yet I'm backing up bookmarks..which is a FIREFOX function. Backing up bookmarks in FireFox will do nothing for me when I create a new profile in Thunderbird.

I've only been using TB and FF for about 5 years but maybe I'm missing something and you can clue me in.

---

### Post by presence1960 on 2009-07-09
> **American said:**
> You're not making any sense to me...

I'm creating a new profile for THUNDERBIRD...yet I'm backing up bookmarks..which is a FIREFOX function. Backing up bookmarks in FireFox will do nothing for me when I create a new profile in Thunderbird.

I've only been using TB and FF for about 5 years but maybe I'm missing something and you can clue me in.

no you're not missing something. I was helping on two threads and got off the beaten path on this one. My bad, I am sorry for the confusion.

---

### Post by American on 2009-07-09
Ok.. so now that we cleared all of that up.

So I create a new profile in TB... I have about 10GB of email and 8 accounts.

If I create a new profile and then copy/paste the contents of my xxxx.default dir into my xxxx.new profile dir I'm basically going to have the same thing...just in renamed folder.

How is that going to help?

---

### Post by presence1960 on 2009-07-09
> **American said:**
> Ok.. so now that we cleared all of that up.

So I create a new profile in TB... I have about 10GB of email and 8 accounts.

If I create a new profile and then copy/paste the contents of my xxxx.default dir into my xxxx.new profile dir I'm basically going to have the same thing...just in renamed folder.

How is that going to help?

I don't know if that will help I posted to answer the question of how to create a new profile.

---

### Post by American on 2009-07-10
Eh... I just moved everything over to Evolution, simple. Maybe when one day someone comes up with a real fix I'll move back to TB.

---

### Post by JCBrand on 2009-07-20
I've managed to fix the problem... for me at least.

I switched to evolution to test if opening links works there, and got the following error:

[FONT="Courier New"]
Failed to execute child process "/opt/firefox/firefox" (No such file or directory)[/FONT]

So I created the firefox dir and a symlink in opt:

sudo mkdir /opt/firefox
sudo ln -s /usr/bin/firefox /opt/firefox/firefox

And now links in Thunderbird are opened again in FF :)

---

### Post by American on 2009-07-20
That still didn't work...but then again my Evolution install is working fine opening links in FF. I even went back an used /usr/bin/firefox in the config editor for FF and that didn't work either.

Seems someone might give a $&!+ about this and come up with a real fix.

---

