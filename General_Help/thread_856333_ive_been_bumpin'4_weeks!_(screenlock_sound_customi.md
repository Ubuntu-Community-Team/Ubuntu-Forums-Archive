---
title: "ive been bumpin'4 weeks! (screenlock sound customization)"
date: 2008-07-11
forum: General Help
---

### Post by adamogardner on 2008-07-11
hi  i joined in mayu and don't know if this is right to post here after many many hits and no replies.  I have the Coolest idea.  I have a robot that can say (in a vikki from irobot voice) "shields activated" and "shields deactivated"  ThIs WoUlD bE pErFeCt   incidently I noticed in the sound effect customizer thing there is a power down option but when I power down there is no time to sound off "system terminated" before it shuts.  Can this be adjusted?  
thanks, and if I'm not supposed to post here, just let me know.

---

### Post by -grubby on 2008-07-11
This is the wrong forum for this, yes. Not sure about your problem. I've reported it to be moved (don't worry, you won't get in trouble or anything)

---

### Post by p_quarles on 2008-07-11
Moved to Desktop Effects & Customization. 

The Unanswered Posts Team forum is for the team that handles such things, not for unanswered posts. Also, bumping actually prevents that team from finding your post.

---

### Post by ad_267 on 2008-07-11
If you go to System - Preferences - Sounds, there is an option for "Log out" and "Log in" sounds.

---

### Post by adamogardner on 2008-07-12
yes of course there is.  here's what I wrote when I started this thread:

"incidently I noticed in the sound effect customizer thing there is a power down option but when I power down there is no time to sound off "system terminated" before it shuts. Can this be adjusted?"

the sound is set, but when I hit reatart or shut down, the shutdown is rather instant and gives no time for the bows

---

### Post by ad_267 on 2008-07-12
> **adamogardner said:**
> yes of course there is.  here's what I wrote when I started this thread:

"incidently I noticed in the sound effect customizer thing there is a power down option but when I power down there is no time to sound off "system terminated" before it shuts. Can this be adjusted?"

the sound is set, but when I hit reatart or shut down, the shutdown is rather instant and gives no time for the bows

Ok sorry, yeah I wasn't sure if you were referring to the log of sound or another sound. Sounds like this might be a bug if it doesn't wait for the sound to finish before logging off. You could report this at [https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Don't know if this would work but you could try modifying the script at /etc/gdm/PostSession/Default and add "sleep 10" which should pause for 10 seconds before logging out.

---

### Post by adamogardner on 2008-07-12
i didn't get far:

adamogardner@CRONUS:~$ cd /etc/gdm/PostSession/Default
bash: cd: /etc/gdm/PostSession/Default: Not a directory

---

### Post by ad_267 on 2008-07-12
> **adamogardner said:**
> i didn't get far:

adamogardner@CRONUS:~$ cd /etc/gdm/PostSession/Default
bash: cd: /etc/gdm/PostSession/Default: Not a directory

That's a file, not a directory. It's a bash script.

```
gksudo gedit /etc/gdm/PostSession/Default
```

Then add "sleep 10" before "exit 0"

And I don't know if this will actually work for sure.

---

### Post by adamogardner on 2008-07-13
ok cool i did that. it did what it was supposed to do but didn't work out with the sound.  maybe your on the right track.  how did you know that file?  It sesems complex.  So with the right bash script ubuntu can be tweeked in these customized fashions?

---

### Post by ad_267 on 2008-07-13
So what happened? Did it pause before logging out but then the sound played afterwards and was cut off?

I found that file just by searching for how to run a script on logout. A lot of things in Ubuntu are controlled by scripts like this.

You could try playing the sound from in that script but that would be annoying to change and would play the sound for all users.

---

### Post by adamogardner on 2008-07-13
yes it paused 10 seconds before logout.  there was no sound though.  I want the sound for all users (me) so thats no problem.  Thankyou for pointing me in the right direction, but let me ask:  In what way would it be annoying to change it?  I am concerned only with disaster potential, and completion potential.  I am enthused about learning to do stuff with Linux, as well as my Idea, so there is no trepidation about jumping in and getting my hands dirty as long as it's doable and carries minimum to average risk.

---

### Post by ad_267 on 2008-07-13
I just meant you would have to edit the line in /etc/gdm/PostSession/Default to change the sound rather than the usual dialog.

What I would try is installing the package sox, "sudo apt-get install sox libsox-fmt-all" then you can add "play /path/to/sound/file" before "exit 0" to play the sound. You can type "man play" to get more information on the play command.

---

### Post by adamogardner on 2008-07-13
I'm trying to write a path to sound file.  I'm testing it by tryint to CD there.  It's not working so I wonder if I'm starting correctly or I'm malformed...

adamogardner@CRONUS:/$ cd /adamogardner/Documents/Female Computer or Robot says Connection Disengaged-Reverb.wav
bash: cd: /adamogardner/Documents/Female: No such file or directory

or:

adamogardner@CRONUS:/$ cd /home/adamogardner/Documents/Female Computer or Robot says Connection Disengaged-Reverb.wav
bash: cd: /home/adamogardner/Documents/Female: No such file or directory

To the best of my knowledge I downloaded sox, though I don;t know if it's active  I just did what you said.

---

### Post by ad_267 on 2008-07-15
> **adamogardner said:**
> I'm trying to write a path to sound file.  I'm testing it by tryint to CD there.  It's not working so I wonder if I'm starting correctly or I'm malformed...

adamogardner@CRONUS:/$ cd /adamogardner/Documents/Female Computer or Robot says Connection Disengaged-Reverb.wav
bash: cd: /adamogardner/Documents/Female: No such file or directory

or:

adamogardner@CRONUS:/$ cd /home/adamogardner/Documents/Female Computer or Robot says Connection Disengaged-Reverb.wav
bash: cd: /home/adamogardner/Documents/Female: No such file or directory

To the best of my knowledge I downloaded sox, though I don;t know if it's active  I just did what you said.

Put the full path in quotes because it has spaces. Try
```
play "/home/adamogardner/Documents/Female Computer or Robot says Connection Disengaged-Reverb.wav"
```

Also if you use cd and start it with /, it will be relative to the root. If you are in /home/adamogardner and want to cd to Documents you use "cd Documents", not "cd /Documents"

---

### Post by alt3rn1ty on 2008-08-21
Found a bug report on the shut down sound issue, lot of people having the same problem, but a possible solution (not for hardy 8.04 users though) at the end of the comments.....
[https://bugs.launchpad.net/ubuntu/+bug/214370](https://bugs.launchpad.net/ubuntu/+bug/214370)

---

### Post by adamogardner on 2008-08-21
thankyou for this.

---

