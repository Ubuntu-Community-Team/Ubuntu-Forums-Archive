---
title: "Canon MP560 and LifeCam VX - 3000 in ubuntu 11.04"
date: 2011-09-11
forum: Hardware
---

### Post by international on 2011-09-11
Hi all. I am looking for a set of instructions to install my Canon MP560 and my LifeCam VX - 3000 in ubuntu 11.04. Can anyone of you help me? Please don't forget, I don't know anything. I want instructions step by step.  I have only two things. My right hand on mouse and my left hand on the keyboard. Thank you.

---

### Post by sidestyle on 2012-01-10
Hi!

The webcams should already be "installed." ([See Here]("https://help.ubuntu.com/community/Webcam")) It's just a matter of getting various applications to use them properly.

I don't know if this is too late for you, but I found this advice to be extremely helpful for me (this is a guide to getting the VX-3000 to work in Skype):

[http://askubuntu.com/a/77994/41016](http://askubuntu.com/a/77994/41016)

I had to do two additional things in order for this to work, however, in the final steps:

**What He Did**
Making it permanent
If this works, you can change the Menu entry similar to how @demua suggests doing:

copy /usr/share/applications/skype.desktop to a file in your Profile to prevent future updates from undoing your changes. This can be done in a Terminal with:

mkdir -p $HOME/.local/share/applications
cp /usr/share/applications/skype.desktop $HOME/.local/share/applications/
open the newly created $HOME/.local/share/applications/skype.desktop in an editor and change the line

 Exec=skype
to something like

 Exec=env LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
Of course you have to use the same path here as above when testing.

**What I Did**
Making it permanent
If this works, you can change the Menu entry similar to how @demua suggests doing:

FIRST:
Create the directory in terminal. Type this in and hit enter.
mkdir -p $HOME/.local/share/applications

SECOND:
Type in sudo chmod a+rw /usr/share/applications
Enter your password when asked.
After you hit enter, it should bring you back to the normal terminal prompt. This is good, that means the changes were made.

THIRD:
Type in sudo chmod a+rw $HOME/.local/share/applications

FOURTH:
Go to Places -> Search for files...
Type in "skype.desktop" without quotes.
Right-click and open the one that is in the /usr/share/applications directory with gedit.

FIFTH:
Change the line

 Exec=skype
to something like

 Exec=env LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so skype
Of course you have to use the same path here as above when testing.

Save and Over-write the old file.

SIXTH:
Copy /usr/share/applications/skype.desktop to a file in your Profile to prevent future updates from undoing your changes. 
Type this into terminal:

cp /usr/share/applications/skype.desktop $HOME/.local/share/applications/

---
Now try opening skype and using the test module in settings. 
It worked for me!

I hope this works for you or gives you some idea on how to get your camera working. Anyone, please feel free to correct me on anything I did here in case it is horribly wrong. All I know is this is what I did and now my skype allows me to use my webcam. 

Best of luck!:D

---

