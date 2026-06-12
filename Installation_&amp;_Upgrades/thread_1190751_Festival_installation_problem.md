---
title: "Festival installation problem"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by bjindal on 2009-06-18
Hello

I installed festival on ubuntu with apt-get install festival then installed a voice for American male then typed festival at console to enter festival console then typed   
   (SayText "Hello World") 
in festival console.Then its giving the following error.Plz tell me whats this. How can i run festival?
Linux: can't open /dev/dsp
#<Utterance 0xb6945878>

Thanks in advance 

Bhavana

---

### Post by dstew on 2009-06-18
See [this thread]("http://ubuntuforums.org/showthread.php?t=171182"). There are many fixes that work, including using sudo. The best fix seems to be```
printf ";use ALSA\n(Parameter.set 'Audio_Method 'Audio_Command)\n(Parameter.set 'Audio_Command \"aplay -q -c 1 -t raw -f s16 -r \$SR \$FILE\")\n" > ~/.festivalrc
```Copy and paste this code into a command line.

---

### Post by bjindal on 2009-06-19
Hello

I am new to ubuntu.  Thanks for replying.

I did the following 

bhavana@bhavana-desktop:~$ sudo festival
Festival Speech Synthesis System 1.96:beta July 2004
Copyright (C) University of Edinburgh, 1996-2004. All rights reserved.
For details type `(festival_warranty)'
festival> (SayText "Hello World!")
#<Utterance 0xb69e9c68>
festival> 

The above thing dint work too.
Then, I  pasted the following code in command line
printf ";use ALSA\n(Parameter.set 'Audio_Method 'Audio_Command)\n(Parameter.set 'Audio_Command \"aplay -q -c 1 -t raw -f s16 -r \$SR \$FILE\")\n" > ~/.festivalrc
Then opened festival console and typed the saytext line and it still dint work.

Then i did this 

sudo apt-get install alsa*
It gave some unmet dependencies like


 libboost-signals-dev: Depends: libboost-dev (= 1.34.1-15ubuntu3)
  libboost-signals1.35-dev: Conflicts: libboost-signals-dev but 1.34.1-15ubuntu3 is to be installed
  libboost-signals1.37-dev: Depends: libboost1.37-dev (= 1.37.0-3ubuntu3) but it is not going to be installed
                            Conflicts: libboost-signals-dev but 1.34.1-15ubuntu3 is to be installed
                            Conflicts: libboost-signals1.35-dev but 1.35.0-8ubuntu5 is to be installed
E: Broken packages

I also tried

bhavana@bhavana-desktop:~$ festival &#8211;tts /home/bhavana/Desktop/hello.txt
SIOD ERROR: could not open file &#8211;tts
bhavana@bhavana-desktop:~$ echo "Hello world!" | festival &#8211;tts
bash: !": event not found
bhavana@bhavana-desktop:~$ 


Plz suggest something to do.

Thanks

Bhavana

---

### Post by dstew on 2009-06-19
To install alsa, try this command:```
sudo apt-get install alsa-oss oss-compat
```

---

### Post by bjindal on 2009-06-22
Hello.

Thanks a lot for helping me out and spending your precious time for answering the query. I'm able to run Festival on ubuntu now.

  I installed voice for hindi male to speak hindi and did the following and it gives the following errors:

bhavana@bhavana-desktop:~$ sudo festival --language hindi --tts /home/bhavana/Desktop/hello.txt
"Unsupported language, using English"
SIOD ERROR: unbound variable : voice_rab_diphone
festival: fatal error exiting.



Where is the problem?

Bhavana

---

### Post by bjindal on 2009-06-22
hi

I did the following to get the hindi voice

[B]festival>(voice_hindi_NSK_diphone)
festival>[/B][B](tts "/home/sample.txt" nil)


This made the hindi voice play.But now the English voice doesnot play.

Thank you.

Bhavana
[/B]

---

### Post by bjindal on 2009-06-24
hi

Bump.....

---

