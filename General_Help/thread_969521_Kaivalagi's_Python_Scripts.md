---
title: "Kaivalagi's Python Scripts"
date: 2008-11-03
forum: General Help
---

### Post by kaivalagi on 2008-11-03
[SIZE="1"][COLOR="RoyalBlue"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: **[http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)**

**Ubuntu/Debian : **All the script packages have now been copied into the Conky Companions PPA. Any package updates will be provided by the team through this new ppa. The ppa can be found here: [https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa"). To use this ppa first delete the old ppa files using this: "**sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore***". Then follow the modified first post instructions for the scripts[/COLOR][/SIZE]

As the number of scripts I've created for Conky has grown, I figured I would create a thread to link to all the scripts threads.

So here they are:
[SIZE=2][B]
[LIST]
[*][[SIZE=2]**conkyBanshee**[/SIZE]]("http://ubuntuforums.org/showthread.php?p=7683570")
[*][[SIZE=2]**conkyClementine**[/SIZE]]("http://ubuntuforums.org/showthread.php?p=10239175")
[*][conkyDeluge]("http://ubuntuforums.org/showthread.php?t=946664")
[*][conkyEmail]("http://ubuntuforums.org/showthread.php?t=869771")
[*][conkyExaile]("http://ubuntuforums.org/showthread.php?t=926041")
[*][conkyForecast]("http://ubuntuforums.org/showthread.php?t=869328")
[*][conkyGoogleCalendar]("http://ubuntuforums.org/showthread.php?t=837385")
[*][conkyGoogleReader]("http://ubuntuforums.org/showthread.php?p=9800463")
[*][conkyGuayadeque]("http://ubuntuforums.org/showthread.php?p=9668167")
[*][conkyMisc]("http://ubuntuforums.org/showthread.php?p=10244850")
[*][conkyPidgin]("http://ubuntuforums.org/showthread.php?p=6099901")
[*][conkyRhythmbox]("http://ubuntuforums.org/showthread.php?t=928168")
[*][conkyTransmission]("http://ubuntuforums.org/showthread.php?p=10215207")
[/LIST]
[/B][/SIZE]
All are available via the Conky Companions PPA, which can be setup in two simple steps.

1) Add the repository to your OS install:
```
sudo add-apt-repository ppa:conky-companions/ppa
```
* Note if you are running 9.10 or below then refer to the PPA link at the end of this post for help on installing from the ppa, good guidance can be found on the launchpad site

2) Now that is done simply run the following to update your repo cache and install. To install conkyForecast for example: 

```
sudo apt-get update && sudo apt-get install conkyforecast

```If you have any suggestions for new scripts, just post them here.

At the Conky Companion PPA site you will find source code, packages and tarballs too. It can be found here: [COLOR="Blue"]**[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**[/COLOR]

If you require assistance with any of the scripts, please read their respective threads, and if necessary, post in them. **[COLOR=Red]I will not answer your script specific questions here, I will just ask you go to the correct thread![/COLOR]**

---

### Post by jrhorner on 2008-11-08
Do you have or know of a script that can check how many system updates are available? Thanks in advance.

---

### Post by jrhorner on 2008-11-08
Forgot to say for Interpid system.

---

### Post by kaivalagi on 2008-11-08
> **jrhorner said:**
> Do you have or know of a script that can check how many system updates are available? Thanks in advance.

Knocked up the attached in 10 minutes...needs work though. I am not sure whether it will actually update the apt cache too though, so will only show what the system updates would once they've done their thing.


You might find a command line function that will do a nicer job...but I dont know of one other than the standard apt-get/aptitude functions (you can use these with a -s option to simulate only)

---

### Post by jrhorner on 2008-11-08
Thanks I'll give this a try. I'm new to Linux so reading the scripts and testing in terminal will let me see whats going on so I can learn to do myself.

---

### Post by kaivalagi on 2008-11-08
> **jrhorner said:**
> Thanks I'll give this a try. I'm new to Linux so reading the scripts and testing in terminal will let me see whats going on so I can learn to do myself.

The scripts not great, it displays a lot of stuff you wont want to see...there is no easy way to turn off all the initialisation output

---

### Post by kaivalagi on 2008-12-14
New app added to my PPA, new thread on this can be found through the apps link in my sig below...

---

### Post by kaivalagi on 2009-02-02
**[COLOR="Black"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

New instructions on setting up the repository in your system have been added to the first post, as follows

[COLOR="Black"]**Remove any existing /etc/apt/sources.list entry before or after doing this!**[/COLOR]

1) Create the necessary list file for access to the repository by running this:

```
sudo wget -q http://www.kaivalagi.com/m-buck-ppa.list -O /etc/apt/sources.list.d/m-buck-ppa.list
```

2) Add the repository public key to your apt setup by running this:

```
wget -q http://www.kaivalagi.com/m-buck-ppa-key.gpg -O- | sudo apt-key add -
```

---

### Post by kaivalagi on 2009-04-18
**[COLOR="Green"][SIZE="5"]INSTALL UPDATE[/SIZE][/COLOR]**

**PPA Location Changes**

I have created new PPA's on launchpad to sub-divide all my scripts into their own categories. As such the installation steps for conky scripts have changed, which have been updated on the first post.

You should all change the repository details using the first post steps to get new updates, no new updates will be applied to the old archive location going forwards.

By all means leave the old settings in place too, but these will not help you much.

**Jaunty Package Support**

I have created equivalent packages for Jaunty Jackalope in my PPA's now. They are identical to the intrepid packages but sit under a jaunty location. In my limited testing they all seem to work fine. Again the first post has been updated to describe the setup steps.

Chimo!

---

### Post by iooma on 2009-05-24
any scripts for currency? like xe.com, it gives live currency rates
thanks

---

### Post by WiseGuy1020 on 2009-09-14
Hey K,

I have been showing people your scripts like crazy, everyone seems to love them. I was wondering, any chance of a conkySongbird?


Thanks,
[INDENT]D.[/INDENT]

---

### Post by kaivalagi on 2009-09-14
> **WiseGuy1020 said:**
> Hey K,

I have been showing people your scripts like crazy, everyone seems to love them. I was wondering, any chance of a conkySongbird?


Thanks,
[INDENT]D.[/INDENT]

I may be able to take a look in a month or so, remind me again then. I have just started a new contract and am very busy right now - any spare time is used up by my son or small fixes to the existing scripts. I have taken a quick look at the possibilities and maybe songbird won't work well "as is" for a new script.....but I need to dig deeper before I can say for sure...

Cheers

---

### Post by kaivalagi on 2009-11-01
[COLOR=Red]I have switched OS and now use **ArchLinux** rather than any debian based distro. It looks like the continuing support of my scripts will be **without ppa updates**, and instead my time will support AUR based installs once I get to understand them. I will provide the usual tarball downloads of the source for non Arch users from within these forum.[/COLOR]

---

### Post by kaivalagi on 2010-01-08
[SIZE="1"][COLOR="RoyalBlue"]**ArchLinux : **Package support is present in the AUR. All my packages can be seen here: [http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi](http://aur.archlinux.org/packages.php?SeB=m&K=kaivalagi)[/COLOR][/SIZE]

**[COLOR="Blue"][SIZE="3"]IMPORTANT NEWS[/SIZE]**
All the script packages have now been copied into the Conky Hardcore PPA. Any package updates will be provided by the team through this new ppa.
Instructions to follow / or just figure it out for yourself, the ppa is here: [https://launchpad.net/~conkyhardcore/+archive/ppa]("https://launchpad.net/~conkyhardcore/+archive/ppa")[/COLOR]

---

### Post by VastOne on 2010-07-31
Hi there...

You have scripts for every major player except Guayadeque. 

Would it be possible to take a look at creating a script for G-Que?

I have all the links in how to get dbus to produce all the information, but I do not know the code to write it.

A whole lot of us are looking for the G-Que to Conky holy grail.

Thanks....

---

### Post by kaivalagi on 2010-08-01
I didn't realise Guayadeque was a major player...Trouble is, when there are issues who will fix them...;) Ideally I don't wont more scripts to handle/fix/answer questions for...I'm just too busy and like my weekends, especially in the summer months.

I may be out of work soon, if that is the case then I may have the time...

edit: installed guayadeque and looked at dbus side of things, shouldn't be too hard, I just need the time

---

### Post by VastOne on 2010-08-01
> **kaivalagi said:**
> I didn't realise Guayadeque was a major player...Trouble is, when there are issues who will fix them...;) Ideally I don't wont more scripts to handle/fix/answer questions for...I'm just too busy and like my weekends, especially in the summer months.

I may be out of work soon, if that is the case then I may have the time...

edit: installed guayadeque and looked at dbus side of things, shouldn't be too hard, I just need the time

Once I see the initial settings on the script, I will be able to fix and answer questions.  In the last 24 hours I have learned an incredible amount in trying this myself and I have several friends who are developers and coders and I definitely know how to use Google!!!!

If and when you get the time, I will be able to help in any way, along with the developer of Guayadeque, who is a very good friend of mine.

I appreciate all you do, your family and your time is way more important and we all respect that.

---

### Post by kaivalagi on 2010-08-01
Thanks for the support, I'll just have to do something now :)

I'll keep you posted

---

### Post by kaivalagi on 2010-08-01
Didn't take that long...

Find attached the src tarball which includes a conkyGuayadeque.py, you'll have to run it as "python /a/folder/conkyGuayadeque.py" in conky scripts unless you come up with something else.

I can't get my VM of Ubuntu to kickoff package builds in Launchpad for some reason, all looks fine but nothing...so I can't provide ubuntu packages as yet, I'll need to ask for a build from one of the conkyhardcore members.

If you're running Arch then the aur package is 'conkyguayadeque-bzr', install in the usual way e.g. using yaourt, bauerbill, packer etc

I'll post a new thread for the script once I have a package available to install in ubuntu from the repo.

All the player scripts use the same naming convention for datatype output so any of the help on existing scripts for music info output will cover all bases (conkyBanshee/conkyRhythmbox/conkyExaile)

Help for the script (from the -h option) is as follows (red items are not available through dbus yet, place markers):

```
Usage: conkyGuayadeque.py [options]

Options:
  -h, --help            show this help message and exit
  -t FILE, --template=FILE
                        define a template file to generate output in one call.
                        A displayable item in the file is in the form
                        [--datatype=TI]. The following are possible options
                        within each item: --datatype,--ratingchar. Note that
                        the short forms of the options are not currently
                        supported! None of these options are applicable at
                        command line when using templates.
  -d DATATYPE, --datatype=DATATYPE
                        [default: TI] The data type options are: [COLOR="Red"]ST (status),
                        CA (coverart)[/COLOR], TI (title), AL (album), AR (artist), GE
                        (genre), YR (year), TN (track number), FN (file name),
                        [COLOR="red"]BR (bitrate k/s), LE (length), PP (current position in
                        percent)[/COLOR], PT (current position in time), VO (volume),
                        RT (rating). Not applicable at command line when using
                        templates.
  -r CHAR, --ratingchar=CHAR
                        [default: *] The output character for the ratings
                        scale. Command line option overridden if used in
                        templates.
  -s TEXT, --statustext=TEXT
                        [default: Playing,Paused,Stopped] The text must be
                        comma delimited in the form 'A,B,C'. Command line
                        option overridden if used in templates.
  -n, --nounknownoutput
                        Turn off unknown output such as "Unknown" for title
                        and "0:00" for length. Command line option overridden
                        if used in templates.
  -m LENGTH, --maxlength=LENGTH
                        [default: 0] Define the maximum length of any
                        datatypes output, if truncated the output ends in
                        "..."
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.
```

[COLOR="DarkRed"]**@VastOne - could you highlight the red items listed above to the devs of Guayadeque, viewing the dbus options through d-feet I couldn't see all the data I needed. The status data is something I may still be able to sort out, the percentage I can calculate if I have the length of the song available, but nearly all highlighted items need exposing through the dbus service code I think**[/COLOR]

---

### Post by VastOne on 2010-08-01
> **kaivalagi said:**
> Didn't take that long...

Find attached the src tarball which includes a conkyGuayadeque.py, you'll have to run it as "python /a/folder/conkyGuayadeque.py" in conky scripts unless you come up with something else.

I can't get my VM of Ubuntu to kickoff package builds in Launchpad for some reason, all looks fine but nothing...so I can't provide ubuntu packages as yet, I'll need to ask for a build from one of the conkyhardcore members.

If you're running Arch then the aur package is 'conkyguayadeque-bzr', install in the usual way e.g. using yaourt, bauerbill, packer etc

I'll post a new thread for the script once I have a package available to install in ubuntu from the repo.

All the player scripts use the same naming convention for datatype output so any of the help on existing scripts for music info output will cover all bases (conkyBanshee/conkyRhythmbox/conkyExaile)

Help for the script (from the -h option) is as follows (red items are not available through dbus yet, place markers):

```
Usage: conkyGuayadeque.py [options]

Options:
  -h, --help            show this help message and exit
  -t FILE, --template=FILE
                        define a template file to generate output in one call.
                        A displayable item in the file is in the form
                        [--datatype=TI]. The following are possible options
                        within each item: --datatype,--ratingchar. Note that
                        the short forms of the options are not currently
                        supported! None of these options are applicable at
                        command line when using templates.
  -d DATATYPE, --datatype=DATATYPE
                        [default: TI] The data type options are: [COLOR="Red"]ST (status),
                        CA (coverart)[/COLOR], TI (title), AL (album), AR (artist), GE
                        (genre), YR (year), TN (track number), FN (file name),
                        [COLOR="red"]BR (bitrate k/s), LE (length), PP (current position in
                        percent)[/COLOR], PT (current position in time), VO (volume),
                        RT (rating). Not applicable at command line when using
                        templates.
  -r CHAR, --ratingchar=CHAR
                        [default: *] The output character for the ratings
                        scale. Command line option overridden if used in
                        templates.
  -s TEXT, --statustext=TEXT
                        [default: Playing,Paused,Stopped] The text must be
                        comma delimited in the form 'A,B,C'. Command line
                        option overridden if used in templates.
  -n, --nounknownoutput
                        Turn off unknown output such as "Unknown" for title
                        and "0:00" for length. Command line option overridden
                        if used in templates.
  -m LENGTH, --maxlength=LENGTH
                        [default: 0] Define the maximum length of any
                        datatypes output, if truncated the output ends in
                        "..."
  -v, --verbose         Request verbose output, not a good idea when running
                        through conky!
  -V, --version         Displays the version of the script.
  --errorlogfile=FILE   If a filepath is set, the script appends errors to the
                        filepath.
  --infologfile=FILE    If a filepath is set, the script appends info to the
                        filepath.
```

[COLOR="DarkRed"]**@VastOne - could you highlight the red items listed above to the devs of Guayadeque, viewing the dbus options through d-feet I couldn't see all the data I needed. The status data is something I may still be able to sort out, the percentage I can calculate if I have the length of the song available, but nearly all highlighted items need exposing through the dbus service code I think**[/COLOR]

Where to start!

A bazillion thank you's first and foremost.

I was able to take most of the scripts and see what was happening by a trial and error process (my favorite and best way of learning).

I was able to get a Conky screen with Guayadeque and it is attached.

This is a hack of yours but in the short term it is showing progress and is no where near the end result.

The developer, Anonbeat, is on a well deserved holiday and is out of touch for 2 more weeks.  On top of his full time job, family and 10 hours a day working on G-Que, we all wonder if he is superman.. This vacation is a blessing...When he returns, I will work with him on the dbus calls.

This is a development for me as well, trying a whole new area after 22 years as a consultant implementing e-mail, security and disaster recovery platforms..

I have learned an incredible amount in a very short period of time and look forward to more.  Once Anonbeat gets back and we get the ppa lined up for an easier install, I think it will be easier as I had path issues with the tar method (3) just as you predicted.  And there were errors in the py script with banshee messages, but those are not an issue now

For now, there is nothing more to be done until when you want to...

Thank you....

---

### Post by VastOne on 2010-08-01
One other note, I could not get the template to work at all. I tried several ways for several hours but it would never show and I kept get an error


```
sh: conkyGuayadeque: not found
```

even though I was sure it was right, and no matter where I put it, I got the error.

This is why you see the Artist as the first line replacing the template.

Just an FYI.

---

### Post by kaivalagi on 2010-08-02
> **VastOne said:**
> One other note, I could not get the template to work at all. I tried several ways for several hours but it would never show and I kept get an error


```
sh: conkyGuayadeque: not found
```

even though I was sure it was right, and no matter where I put it, I got the error.

This is why you see the Artist as the first line replacing the template.

Just an FYI.

Everywhere you reference conkyGuayadeque it needs to be "python /a/folder/conkyGuayadeque.py" instead...the /usr/bin/conkyGuayadeque file is not present unless to extract that from the tarball and put it in /usr/bin and then it's needs to point to the correct .py path

edit: Thread in place for the script now, just waiting for launchpad package publishing: [http://ubuntuforums.org/showthread.php?p=9668167](http://ubuntuforums.org/showthread.php?p=9668167)

---

### Post by kaivalagi on 2010-08-03
The Conky Guayadeque Script is now available in a package, follow the instructions found here: [http://ubuntuforums.org/showthread.php?t=1544149](http://ubuntuforums.org/showthread.php?t=1544149)

---

### Post by VastOne on 2010-08-03
> **kaivalagi said:**
> The Conky Guayadeque Script is now available in a package, follow the instructions found here: [http://ubuntuforums.org/showthread.php?t=1544149](http://ubuntuforums.org/showthread.php?t=1544149)

Just to let you know...


```
conky -c /usr/share/conkyguayadeque/example/conkyrc &

```
Loaded everything perfectly once I installed using method one!


Thank you!

---

### Post by kaivalagi on 2010-08-03
> **VastOne said:**
> Just to let you know...
```
conky -c /usr/share/conkyguayadeque/example/conkyrc &

```
Loaded everything perfectly once I installed using method one!
Thank you!

Nice one, just need to have a chat with the devs to get the missing items (in red text) into the dbus service methods. The items that are in red are in the first post of the new thread, probably a good idea to post there from now on

Have fun :)

---

### Post by VastOne on 2010-08-03
> **kaivalagi said:**
> Nice one, just need to have a chat with the devs to get the missing items (in red text) into the dbus service methods. The items that are in red are in the first post of the new thread, probably a good idea to post there from now on

Have fun :)

I let everyone in the Guayadeque forum know to post here or at the main conky thread for issues and as soon as Anonbeat gets back from vacation the missing variables should be done within a day

Thanks!

---

### Post by kaivalagi on 2010-08-03
> **VastOne said:**
> I let everyone in the Guayadeque forum know to post here or at the main conky thread for issues and as soon as Anonbeat gets back from vacation the missing variables should be done within a day

Thanks!

Dont post here, post [here]("http://ubuntuforums.org/showthread.php?p=9668167")

Look forward to the fixes :)

---

### Post by VastOne on 2010-08-03
> **kaivalagi said:**
> Dont post here, post [here]("http://ubuntuforums.org/showthread.php?p=9668167")

Look forward to the fixes :)

Yes...That is the link I have for them to post at, I was confused where i was at with so many tabs open!

Thanks!

---

### Post by wlourf on 2010-08-29
*wrong topic, sorry :( didn't find the way to delete a message*

---

### Post by kaivalagi on 2010-09-03
I've added a conkyGoogleReader thread to the list now, to support this script going forwards. The script has been around for a while and only now I feel it is supportable :)

---

### Post by VastOne on 2010-12-07
Hi K...

Another player that is getting major traction is Clementine which is a fork of the old Amarok 1.4 that has been re written...
 
I am using this opportunity to get a handle on your python scripts and I am making headway with it...

Clementine seems to "send" it's dbus data in this method


  AddMetadata("location", song.filename(), &ret);
  AddMetadata("title", song.PrettyTitle(), &ret);
  AddMetadata("artist", song.artist(), &ret);
  AddMetadata("album", song.album(), &ret);
  AddMetadata("time", song.length(), &ret);
  AddMetadata("mtime", song.length() * 1000, &ret);
  AddMetadata("tracknumber", song.track(), &ret);
  AddMetadata("year", song.year(), &ret);
  AddMetadata("genre", song.genre(), &ret);
  AddMetadata("disc", song.disc(), &ret);
  AddMetadata("comment", song.comment(), &ret);
  AddMetadata("audio-bitrate", song.bitrate(), &ret);
  AddMetadata("audio-samplerate", song.samplerate(), &ret);
  AddMetadata("bpm", song.bpm(), &ret);
  AddMetadata("composer", song.composer(), &ret);
  AddMetadata("artUrl",

As you can see, it has all but Status in this metadata.  

My question is, it looks as if the song. header is what is needed to replace musicData. that is in the Guayadeque script, would you agree with what I am seeing and the direction I am heading?

Edit - More info

Running this 

```
dbus-send --print-reply --dest=org.mpris.clementine /TrackList org.freedesktop.MediaPlayer.GetMetadata int32:0
```

Gives me the output needed 
```

method return sender=:1.165293 -> dest=:1.180511 reply_serial=2
   array [
      dict entry(
         string "album"
         variant             string "Sunset Reposed"
      )
      dict entry(
         string "artUrl"
         variant             string "(embedded)"
      )
      dict entry(
         string "artist"
         variant             string "Caustic Reverie"
      )
      dict entry(
         string "audio-bitrate"
         variant             int32 191
      )
      dict entry(
         string "audio-samplerate"
         variant             int32 44100
      )
      dict entry(
         string "comment"
         variant             string "http://www.jamendo.com/"
      )
      dict entry(
         string "genre"
         variant             string "Ambient"
      )
      dict entry(
         string "location"
         variant             string "/media/storage/Music/mp3new/All Ambient/Caustic Reverie/Sunset Reposed/01 - Suspend Stereo.mp3"
      )
      dict entry(
         string "mtime"
         variant             int32 695000
      )
      dict entry(
         string "time"
         variant             int32 695
      )
      dict entry(
         string "title"
         variant             string "Suspend Stereo"
      )
      dict entry(
         string "tracknumber"
         variant             int32 1
      )
      dict entry(
         string "year"
         variant             int32 2009
      )
   ]

```

Getting closer, just the how now... Thanks

---

### Post by kaivalagi on 2010-12-08
Looking good, you've found the dbus data you need, I suggest using a tool called d-feet to look closely at the functions available via dbus and then take a copy of the guayadeque script and start messing with it proper...

The trickiest bit will be handling the data returned (no 2 players are the same) and populating the musicData object for output

I don't have Clementine installed, I assume it is a KDE player like Amarok was? If that is the case I wont be able to test as I am not installing any KDE contents onto my OS.

The next step for you may well be installing Eclipse and PyDev so you can debug the script you have and troubleshoot that way, it's by far the quickest way to resolve issues and you can look at the contents of variables as you go etc.

Try to figure out what you can using online docs etc, but if you truly get stuck post away :)

---

### Post by VastOne on 2010-12-08
> **kaivalagi said:**
> Looking good, you've found the dbus data you need, I suggest using a tool called d-feet to look closely at the functions available via dbus and then take a copy of the guayadeque script and start messing with it proper...

The trickiest bit will be handling the data returned (no 2 players are the same) and populating the musicData object for output

I don't have Clementine installed, I assume it is a KDE player like Amarok was? If that is the case I wont be able to test as I am not installing any KDE contents onto my OS.

The next step for you may well be installing Eclipse and PyDev so you can debug the script you have and troubleshoot that way, it's by far the quickest way to resolve issues and you can look at the contents of variables as you go etc.

Try to figure out what you can using online docs etc, but if you truly get stuck post away :)

Thanks K. That is my objective this time around to go through it piece by piece to figure it out..

Clementine is not KDE, it is about the same as Guayadeque.. C++ and Qt4 I believe..

I will hit you up if I get stuck but this is a challenge I am looking forward to..

The developer of Guayadeque went nuts on us and a whole bunch of us defected so we are desperate for a new player to meet our needs...

Exaile is OK, but seems stagnant by developers who do not have the time.  If I get more python ready, I may be able to help them a long way down the road, but for now this will be fun

Thanks for the tips and I will let you know how it goes...

Terry

---

### Post by kaivalagi on 2010-12-08
> **VastOne said:**
> Thanks K. That is my objective this time around to go through it piece by piece to figure it out..

Clementine is not KDE, it is about the same as Guayadeque.. C++ and Qt4 I believe..

I will hit you up if I get stuck but this is a challenge I am looking forward to..

The developer of Guayadeque went nuts on us and a whole bunch of us defected so we are desperate for a new player to meet our needs...

Exaile is OK, but seems stagnant by developers who do not have the time.  If I get more python ready, I may be able to help them a long way down the road, but for now this will be fun

Thanks for the tips and I will let you know how it goes...

Terry

I assume the developer had enough of peoples demands all the time? It can be hard developing for free in your own time in the open source community when all you get are requests for more and more changes and nothing to show for it...it feels like the whole world is just using you for their own selfish needs sometimes so don't be so hard on him!

Have you tried using MPD yet? I am sold on the music daemon thing now, having a seperate player connecting into it. I am using mpdcron too which helps a great deal with conky output on song changes etc...not a bit of python in sight for my MPD setup :)

Have fun anyway, I just know I have spent a long time trialling lots of players and in the end the simplest is the best, just like my distro choice ;)

---

### Post by VastOne on 2010-12-08
> **kaivalagi said:**
> I assume the developer had enough of peoples demands all the time? It can be hard developing for free in your own time in the open source community when all you get are requests for more and more changes and nothing to show for it...it feels like the whole world is just using you for their own selfish needs sometimes so don't be so hard on him!

Have you tried using MPD yet? I am sold on the music daemon thing now, having a seperate player connecting into it. I am using mpdcron too which helps a great deal with conky output on song changes etc...not a bit of python in sight for my MPD setup :)

Have fun anyway, I just know I have spent a long time trialling lots of players and in the end the simplest is the best, just like my distro choice ;)

No, it was quite different with this developer.. He closed in on himself and became a control freak.  And anyone trying to objectively help became the enemy.  Implementing iPod features became an obsession and then it became mandatory to install the required libraries even if you did not own an iPod, which is OK until the new libraries cause your memory and I/O to spike off the charts... When I publically questioned these things, I was banned!  So much for OSS

Someday I am sure I will think the same about distro and MPD and the simplicity of it all.. 

Probably about the same time Unity is shoved down my throat...

---

### Post by VastOne on 2010-12-08
> **kaivalagi said:**
> I assume the developer had enough of peoples demands all the time? It can be hard developing for free in your own time in the open source community when all you get are requests for more and more changes and nothing to show for it...it feels like the whole world is just using you for their own selfish needs sometimes so don't be so hard on him!

Have you tried using MPD yet? I am sold on the music daemon thing now, having a seperate player connecting into it. I am using mpdcron too which helps a great deal with conky output on song changes etc...not a bit of python in sight for my MPD setup :)

Have fun anyway, I just know I have spent a long time trialling lots of players and in the end the simplest is the best, just like my distro choice ;)

With your MPD and mpdcron, do you get a similar output as we do now with the Guayadeque and Exaile?  The layout I use I really like on my desktop, if I can get it or something similar, I will switch in a heartbeat..

Can you send me your .conkyrc or whatever you have that calls the music from MPD and the cron?

Thanks

---

### Post by kaivalagi on 2010-12-08
Screenshot attached

conkyrc:
```
TEXT
$if_mpd_playing${image /home/USER/scripts/conky/opaque.png -p 0,0 -s 256x330}
${font Liberation Sans:style=Bold:size=6}${alignr 10}${if_match "$mpd_repeat" == "On"}REPEAT$endif
${alignr 10}${if_match "$mpd_random" == "On"}SHUFFLE$endif
${voffset 203}
${color2}${font}${mpd_bar 10,255}
${voffset 5}${color2}${font}${goto 15}${mpd_elapsed}/${mpd_length} - ${mpd_percent}%${alignr 5}${mpd_status} ${mpd_bitrate}k/s
${voffset 5}${color1}${font Liberation Sans:style=Bold:size=9}${alignc}${mpd_title}
${font}${alignc}${color2} from the album ${color1}${font Liberation Sans:style=Bold:size=9}${mpd_album}
${color2}${font}${alignc} by ${color1}${font Liberation Sans:style=Bold:size=9}${mpd_artist}
${color2}${hr}
${if_existing /tmp/lyrics}${image /home/USER/scripts/conky/opaque.png -p 0,330 -s 256x490}${color1}${font Liberation Sans:style=Bold:size=9}${exec fold -s -w 40 /tmp/lyrics | sed 's/^/  /'}
${color2}${hr}$endif
${if_existing /tmp/cover}${image /tmp/cover -p 0,0 -s 256x256 -n}$endif
$endif
```

mpdcron, ~/.mpdcron/hooks/cover.sh script for cover art image:
```
#!/usr/bin/env sh

# get cover (if found) and link it to /tmp/cover
coverfile="$HOME/.covers/$MPD_SONG_TAG_ARTIST-$MPD_SONG_TAG_ALBUM.jpg"
outputcoverfile="/tmp/cover"
if [ -f "$coverfile" ]; then
    rm -f "$outputcoverfile"
    echo "coverart.sh - Linking '$outputcoverfile' to cover file '$coverfile'"
    ln -s "$coverfile" "$outputcoverfile"
else
    echo "coverart.sh - No matching cover art file found here: '$coverfile'"
    rm -f "$outputcoverfile"
fi

```

mpdcron, ~/.mpdcron/hooks/lyrics.sh script for lyrics:
```
#!/usr/bin/env sh

# get lyrics (if found) and link it to /tmp/lyrics
lyricsfile="$HOME/.lyrics/$MPD_SONG_TAG_ARTIST-$MPD_SONG_TAG_TITLE.txt"
outputlyricsfile="/tmp/lyrics"
if [ -f "$lyricsfile" ]; then
    rm -f "$outputlyricsfile"
    echo "lyrics.sh - Linking '$outputlyricsfile' to cover file '$lyricsfile'"
    ln -s "$lyricsfile" "$outputlyricsfile"
else
    rm -f "$outputlyricsfile"
fi
```

MPDCron will fire on a song change and the cover art and lyrics scripts are run to update the sym links. More info on mpdcron can be found here: [http://alip.github.com/mpdcron/](http://alip.github.com/mpdcron/)

I use Sonata as a player GUI, simple and lightweight. I also can stream the music MPD plays via icecast (mpd has support for this) easily and can also manage MPD remotely using my Android phone (using Droid MPD Client) so in theory if I had unlimited bandwidth on my phone could listen to my home collection ;)

---

### Post by kaivalagi on 2010-12-08
Just added the conkyTransmission script to the fold - pay close attention to the requirements and gotcha section in it's thread before using it though...

---

### Post by VastOne on 2010-12-08
> **kaivalagi said:**
> Screenshot attached

conkyrc:
```
TEXT
$if_mpd_playing${image /home/USER/scripts/conky/opaque.png -p 0,0 -s 256x330}
${font Liberation Sans:style=Bold:size=6}${alignr 10}${if_match "$mpd_repeat" == "On"}REPEAT$endif
${alignr 10}${if_match "$mpd_random" == "On"}SHUFFLE$endif
${voffset 203}
${color2}${font}${mpd_bar 10,255}
${voffset 5}${color2}${font}${goto 15}${mpd_elapsed}/${mpd_length} - ${mpd_percent}%${alignr 5}${mpd_status} ${mpd_bitrate}k/s
${voffset 5}${color1}${font Liberation Sans:style=Bold:size=9}${alignc}${mpd_title}
${font}${alignc}${color2} from the album ${color1}${font Liberation Sans:style=Bold:size=9}${mpd_album}
${color2}${font}${alignc} by ${color1}${font Liberation Sans:style=Bold:size=9}${mpd_artist}
${color2}${hr}
${if_existing /tmp/lyrics}${image /home/USER/scripts/conky/opaque.png -p 0,330 -s 256x490}${color1}${font Liberation Sans:style=Bold:size=9}${exec fold -s -w 40 /tmp/lyrics | sed 's/^/  /'}
${color2}${hr}$endif
${if_existing /tmp/cover}${image /tmp/cover -p 0,0 -s 256x256 -n}$endif
$endif
```

mpdcron, ~/.mpdcron/hooks/cover.sh script for cover art image:
```
#!/usr/bin/env sh

# get cover (if found) and link it to /tmp/cover
coverfile="$HOME/.covers/$MPD_SONG_TAG_ARTIST-$MPD_SONG_TAG_ALBUM.jpg"
outputcoverfile="/tmp/cover"
if [ -f "$coverfile" ]; then
    rm -f "$outputcoverfile"
    echo "coverart.sh - Linking '$outputcoverfile' to cover file '$coverfile'"
    ln -s "$coverfile" "$outputcoverfile"
else
    echo "coverart.sh - No matching cover art file found here: '$coverfile'"
    rm -f "$outputcoverfile"
fi

```

mpdcron, ~/.mpdcron/hooks/lyrics.sh script for lyrics:
```
#!/usr/bin/env sh

# get lyrics (if found) and link it to /tmp/lyrics
lyricsfile="$HOME/.lyrics/$MPD_SONG_TAG_ARTIST-$MPD_SONG_TAG_TITLE.txt"
outputlyricsfile="/tmp/lyrics"
if [ -f "$lyricsfile" ]; then
    rm -f "$outputlyricsfile"
    echo "lyrics.sh - Linking '$outputlyricsfile' to cover file '$lyricsfile'"
    ln -s "$lyricsfile" "$outputlyricsfile"
else
    rm -f "$outputlyricsfile"
fi
```

MPDCron will fire on a song change and the cover art and lyrics scripts are run to update the sym links. More info on mpdcron can be found here: [http://alip.github.com/mpdcron/](http://alip.github.com/mpdcron/)

I use Sonata as a player GUI, simple and lightweight. I also can stream the music MPD plays via icecast (mpd has support for this) easily and can also manage MPD remotely using my Android phone (using Droid MPD Client) so in theory if I had unlimited bandwidth on my phone could listen to my home collection ;)

Got everything going except covers... I think I may need the steps in how you are calling this cover.sh and do I need to create this .covers directory?

I am missing the how-to in getting mpdcron to start this

It also appears that embedded files are not accessible? 

I will be online all night so I will see you ...

Thanks

MPD rocks!

---

### Post by kaivalagi on 2010-12-09
> **VastOne said:**
> Got everything going except covers... I think I may need the steps in how you are calling this cover.sh and do I need to create this .covers directory?

I am missing the how-to in getting mpdcron to start this

It also appears that embedded files are not accessible? 

I will be online all night so I will see you ...

Thanks

MPD rocks!

The 2 scripts for lyrics and covers go into ~/.mpdcron/hooks/:
```
~/.mpdcron/hooks]$ ls
total 32
drwxr-xr-x 2 mark users 4096 Oct 25 23:54 .
drwxr-xr-x 3 mark users 4096 Dec  9 07:41 ..
-rwxr-xr-x 1 mark users 1751 Oct 25 23:51 coverart.sh
-rwxr-xr-x 1 mark users  394 Oct 25 23:54 lyrics.sh
-rwxr-xr-x 1 mark users   54 Jan  5  2010 player

```

But if you notice above there is a player script there too, forgot about that, it has the following contents and should explain why the scripts weren't running for you!:
```
#!/usr/bin/env sh
hooks/coverart.sh
hooks/lyrics.sh

```

What do you mean by embedded files?

The .covers folder is one I setup with Sonata, so when it fetches coverart it is placed in there...I've attached the appropriate setting screen from the player

The install of mpdcron on Arch was simple, there was an AUR PKGBUILD file someone created for it, there is nothing in Ubuntu so you have to compile it, here's the PKGBUILD file contents as they may help you in the build although this is basic instructions on the site I linked:
```
#Contributor: Rasi <rasi@xssn.at>

pkgname=mpdcron-git
arch=('i686' 'x86_64')
pkgver=20100611
pkgrel=1
pkgdesc="mpd 'cron-daemon' that listens for events and executes user defined stuff"
source=()
url="http://alip.github.com/mpdcron/"
license="GPL"
depends=('libmpdclient>=2.1' 'libdaemon' 'glib2' 'curl' 'sqlite3')
makedepends=('gcc' 'make' 'autoconf')
md5sums=()
options=('!libtool')

#_gitroot="git://git.lizardhost.co.uk/mpdcron.git"
#_gitname="mpdcron"
_gitroot="git://github.com/alip/mpdcron.git"
_gitname="mpdcron"

build() {
  cd ${srcdir}
  msg "Connecting to $pkgname GIT server...."

  if [ -d ${srcdir}/$_gitname ] ; then
          cd $_gitname && git pull origin
          msg "The local files are updated."
  else
          git clone $_gitroot
  fi

  msg "GIT checkout done or server timeout"

  cp -r ${srcdir}/$_gitname ${srcdir}/$_gitname-build
  cd ${srcdir}/$_gitname-build

  msg "Starting autogen.sh..."
  ./autogen.sh
  msg "Starting configure..."
  ./configure --prefix=/usr --enable-gmodule --with-standard-modules=all
  msg "Starting make..."

  make DESTDIR=$pkgdir install || return 1

  install -D -m644 conf/mpdcron.conf $pkgdir/usr/share/doc/mpdcron/mpdcron.conf
  cp -af conf/hooks $pkgdir/usr/share/doc/mpdcron
}
```

---

### Post by VastOne on 2010-12-09
> **kaivalagi said:**
> The 2 scripts for lyrics and covers go into ~/.mpdcron/hooks/:
```
~/.mpdcron/hooks]$ ls
total 32
drwxr-xr-x 2 mark users 4096 Oct 25 23:54 .
drwxr-xr-x 3 mark users 4096 Dec  9 07:41 ..
-rwxr-xr-x 1 mark users 1751 Oct 25 23:51 coverart.sh
-rwxr-xr-x 1 mark users  394 Oct 25 23:54 lyrics.sh
-rwxr-xr-x 1 mark users   54 Jan  5  2010 player

```

But if you notice above there is a player script there too, forgot about that, it has the following contents and should explain why the scripts weren't running for you!:
```
#!/usr/bin/env sh
hooks/coverart.sh
hooks/lyrics.sh

```

What do you mean by embedded files?

OK, Thanks.. 

So I create this player script and it fires off automatically, with MPDCron running, I am guessing this to be correct

Embedded cover art in the files I mean...

Thanks so much!

---

### Post by kaivalagi on 2010-12-09
> **VastOne said:**
> OK, Thanks.. 

So I create this player script and it fires off automatically, with MPDCron running, I am guessing this to be correct

Embedded cover art in the files I mean...

Thanks so much!

No embedded cover art...but you could adapt one of the getcover python scripts to get the art based on a filepath passed in from mpdcron ;) SOmething for you to figure out....if you get stuck PM me as this is not the place to discuss this any more...

p.s. more added to previous post...

---

### Post by zyghom on 2010-12-09
hi Kaivalgi

for the script with Exaile I get continuous errors:

```
SyntaxError: invalid syntax
  File "/home/papio/.conky/scripts/conkyExaile.py", line 46
    self.parser.add_option("-t", "--template", dest="template", type="string", metavar="FILE", help=u"define a template file to generate output in one call. A displayable item in the file is in the form [--datatype=TI]. The following are possible options within each item: --datatype,--ratingchar. Note that the short forms of the options are not currently supported! None of these options are applicable at command line when using templates.")
```
 
what is the problem ?

---

### Post by kaivalagi on 2010-12-09
> **zyghom said:**
> hi Kaivalgi

for the script with Exaile I get continuous errors:

```
SyntaxError: invalid syntax
  File "/home/papio/.conky/scripts/conkyExaile.py", line 46
    self.parser.add_option("-t", "--template", dest="template", type="string", metavar="FILE", help=u"define a template file to generate output in one call. A displayable item in the file is in the form [--datatype=TI]. The following are possible options within each item: --datatype,--ratingchar. Note that the short forms of the options are not currently supported! None of these options are applicable at command line when using templates.")
```
 
what is the problem ?

As mentioned in the first post of this thread please post issues with specific scripts in their threads ;)

I've posted a reply to this question there...[http://ubuntuforums.org/showthread.php?p=10218096](http://ubuntuforums.org/showthread.php?p=10218096)

---

### Post by kaivalagi on 2010-12-14
**[COLOR="Red"][SIZE="3"]IMPORTANT NEWS[/SIZE][/COLOR]**

All the script packages have now been copied into the **Conky Companions PPA**. Any package updates will be provided by the team through this new ppa. The ppa can be found here: **[https://launchpad.net/~conky-companions/+archive/ppa]("https://launchpad.net/~conky-companions/+archive/ppa")**. To use this ppa first delete the old ppa files using this: 

```
sudo rm /etc/apt/sources.list.d/m-buck* && sudo rm /etc/apt/sources.list.d/conkyhardcore*

```
Then follow the modified first post instructions for the scripts

[COLOR="Red"]**Script updates will only be published through this new ppa going forwards**[/COLOR]

---

### Post by kaivalagi on 2010-12-16
[SIZE="4"]**[COLOR="Green"]SCRIPT ADDED[/COLOR]**[/SIZE]

I've just added the thread for conkyMisc ([http://ubuntuforums.org/showthread.php?p=10244850](http://ubuntuforums.org/showthread.php?p=10244850)) - it's a package containing a few miscellaneous scripts which could well prove useful to some...if you have any suitable scripts (bash/python etc) let me know and I can add them in.

---

### Post by Sector11 on 2011-04-08
[center][ Nouveau : Conky Pitstop - c'est bilingue. ](http: // conky.pitstop.free.fr/fr)
[img]http://dl.dropbox.com/u/16070765/full_CPS-Flag.png[/img]
[New: Conky Pitstop - it's bilingual.](http://conky.pitstop.free.fr/)[/center]

---

### Post by Hazzabin on 2011-09-24
Guys I have searched I'm sure everywhere, with the increase of a variety of 'conky's'
how does one create a command so that 2 or 4 conky's start at startup

many thanks in advance

Hazz

I located what I needed in a very very old post

---

### Post by vehemoth on 2011-09-24
> **Hazzabin said:**
> Guys I have searched I'm sure everywhere, with the increase of a variety of 'conky's'
how does one create a command so that 2 or 4 conky's start at startup

many thanks in advance

Hazz
There's a -c option in conky which tells it to load a specific config file. This allows you to create the multiple instances you desire.

If you want to learn about this sort of stuff it's detailed in the "post your .conkyrc" thread in the community cafe.

---

### Post by Hazzabin on 2011-09-24
Thanks mate, you know for days I've searched.....and yes I had just found it   duh

---

### Post by emk2203 on 2011-11-02
Maybe I'm missing something, but if you use Oneiric, all you can install is conkyforecast since all the others are not in the Oneiric branch of the Conky Companions ppa repository? 

Is that true, or are they obsoleted, or am I supposed to install now by other means?

I'm a little confused here...

---

### Post by kaivalagi on 2011-11-04
> **emk2203 said:**
> Is that true, or are they obsoleted, or am I supposed to install now by other means?

I'm a little confused here...

That's because the packages need copying over to the new release or alternatively you can just point to the previous version

I'll look to copy the binaries over so you see them - [COLOR="Blue"]DONE, should be built in an hour at most[/COLOR]

---

### Post by emk2203 on 2011-11-04
> **kaivalagi said:**
> That's because the packages need copying over to the new release or alternatively you can just point to the previous version

I'll look to copy the binaries over so you see them - [COLOR="Blue"]DONE, should be built in an hour at most[/COLOR]

Thank you! I could have pointed myself to the previous version, but wanted confirmation from The Master to avoid exotic errors if something changed...;)

EDIT: And now the install works like it should, another obstacle in the quest for the perfect conky out of the way!

---

