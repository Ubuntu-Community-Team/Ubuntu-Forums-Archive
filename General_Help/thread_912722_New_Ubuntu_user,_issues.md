---
title: "New Ubuntu user, issues"
date: 2008-09-07
forum: General Help
---

### Post by hd_sheena on 2008-09-07
I've been using ubuntu for about 3 weeks. I got a laptop and it came with Vista, so after considering my options, I decided Ubuntu would be for me. Mostly, it's great, but a couple little things still aren't making sense.
1. I went to install a program "EasyCam" and it told me to add repositories. I followed the directions, but my "Add Remove Apps" box has no "preferences" or "options" button. Help?
So far, that's it, but there will be more I'm sure. Here's some details in case you need them:
Machine: Toshiba Satellite U300
Version: Ubuntu 8.04 - the Hardy Heron
Thanks!
Courtenay W, Canada

---

### Post by Oldsoldier2003 on 2008-09-07
go to system>administration>software sources and add the repos there.

---

### Post by hd_sheena on 2008-09-07
Thanks. That worked perfectly!

---

### Post by hd_sheena on 2008-09-16
I'm trying to install mozilla thunderbird.
I'm sure there is some thing I can type in in terminal that tells my computer to look in the folder (I got it off mozilla website) to install the program, but I don't know what the word is.
When I tried sudo aptitude install, i get various errors. One asks me to be in root, so I tried to log into root, and it told me I can't log into root on that screen. Is there another screen I missed?
Thoughts?

---

### Post by kostkon on 2008-09-16
> **hd_sheena said:**
> I'm trying to install mozilla thunderbird.
I'm sure there is some thing I can type in in terminal that tells my computer to look in the folder (I got it off mozilla website) to install the program, but I don't know what the word is.
When I tried sudo aptitude install, i get various errors. One asks me to be in root, so I tried to log into root, and it told me I can't log into root on that screen. Is there another screen I missed?
Thoughts?
You can install *Thunderbird* using *Synaptic*. Open *Synaptic* and search for it and then select it for installation. 

You don't have to download it from the *Mozilla* website.

One click installation ;)

---

### Post by AllanPoe on 2008-09-16
You can install Thunderbird through Applications>Add/Remove. In the "search" field write "Thunderbird".

---

### Post by hd_sheena on 2008-09-20
Thanks for the thunderbird help. I still can't make it work but thats my settings not my install.
Next question: I go to "sessions preferences" to set which programs start automatically on startup, right? But it wants a "command" and I can't find any for programs like Transmission, Thunderbird, etc.
Help?

---

### Post by hd_sheena on 2008-09-23
i checked and it says i can bump every 24 hours..
How do I change what programs open on startup? see msg above.

---

### Post by ju2wheels on 2008-09-23
1. Figure out the command line name of the program, its usually just the program name itself, lets use Thunderbird as an example. Open Applications->Accessories->Terminal then type:

```

which thunderbird

```

Which then returns the result that the Thunderbird application is located in:
```

/usr/bin/thunderbird

```

So now go to System->Preferences->Sessions. Click Add. Type "Thunderbird" for name. Click on "Browse", select "File System" on the left, then click the usr folder, then the bin folder, and finally select "thunderbird" and press "Open". 

Finally click "Add" and you are done.

Sorry for the long explanation, im sure theres probably a command line way to do all that but I dont know it.

---

### Post by sloggerkhan on 2008-09-23
most applications are actually in your system path so you can  go to sessions in prefs, click add, and type thunderbird under the command if having it load on login is what you're trying to do.

---

### Post by hd_sheena on 2008-09-23
That worked. Thanks!
I'm not sure this is linux or general network issues, but when i open thunderbird, it opens my school network's log in screen, but when i click to log in, it gives me an error. Is it possible this is ubuntu-related, or is it thunderbird, or..?
Thx

---

### Post by sloggerkhan on 2008-09-24
don't know for sure, but it's possible you have your email account's settings wrong. 
Otherwise I'm not sure I'm understanding you.

---

### Post by hd_sheena on 2008-10-16
I used to watch Youtube videos on my ubuntu laptop (I think) and now they don't work anymore. I'm sure I just need a flash extension or something. Thoughts?

---

### Post by jerome1232 on 2008-10-16
Try installing flash and see what happens

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Malac on 2008-10-16
I usually just install all the restricted stuff with: 
```
sudo apt-get install ubuntu-restricted-extras
```This usually sorts out most flash, codecs, java, etc, issues.

Hope this helps.

---

### Post by hd_sheena on 2008-10-16
[sudo] password for home: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So I already have that one. Installing the extras thing now, so maybe that will work.

---

### Post by hd_sheena on 2008-10-16
No suck luck. still wont work, but it does say something about "gnash" in the right-click options.

---

### Post by jerome1232 on 2008-10-16
gnash is an open source flash player, it's probably conflicting with adobe's flash player. try uninstalling gnash.

```
sudo apt-get remove mozilla-plugin-gnash --autoremove
```

---

### Post by hd_sheena on 2008-10-16
home@home:~$ sudo apt-get remove mozilla-plugin-gnash --autoremove
[sudo] password for home: 
\E: Command line option --autoremove is not understood

---

### Post by hd_sheena on 2008-10-16
without auto remove tag at the end, it said it removed it. Now youtube works. Thanks so much!!

---

### Post by jerome1232 on 2008-10-16
oops I must of typoed, I thought you can toss that on at the end of the command. I'm postive it worked for me :)

You might want to do a 'sudo apt-get autoremove' to clear out any un-needed packages.

---

### Post by hd_sheena on 2008-10-22
I'm trying to figure out how to put on drivers for my built-in webcam. I can download drivers to try but dont know how to install them...

---

### Post by Malac on 2008-10-23
> **hd_sheena said:**
> I'm trying to figure out how to put on drivers for my built-in webcam. I can download drivers to try but dont know how to install them...
What file type are they downloaded as?
If it is a .tar file then open them in Archive Manager and extract to a folder depending on the driver it may have an install script inside the top level. They usually need compiling so you will need to install build-essential.```
sudo apt-get install build-essential
```
If it is a .deb file just double click and it should install via GDebi.

Hope this helps.

---

### Post by hd_sheena on 2008-10-24
Camera works now.
I've got some music files on my computer. They default play with "movie player" and I have "rythmbox" as well, and neither will play the music files (a variety of formats) so I got "Audacious" and it wont play them either.
Thoughts?

---

### Post by jerome1232 on 2008-10-24
Thought 1) pull in the codecs
```
sudo apt-get install ubuntu-restricted-extras
```

Thought 2) VLC, it'll play anything :)
```
sudo apt-get install vlc
```

---

### Post by hd_sheena on 2008-10-24
thanks vlc appears to be playing the files.. now a new problem, i have no sound. my speakers work with youtube sound...

---

