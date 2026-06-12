---
title: "program like say the time?"
date: 2008-10-18
forum: General Help
---

### Post by helwitch on 2008-10-18
I'm looking for a program that will read the time at intervals I can set. Ideally, it will also have an alarm feature, but my main need is to hear the actual time every so often. Just a chime every so often isn't good enough, cos I still lose track of the time. When I ran windows, I used Say the Time. I've checked the linux software equivalence lists, and can't find it listed. Help Please.

---

### Post by kartoshka on 2008-10-18
You could try the solution at [http://www.openweblog.com/users/hexmode/512973.html](http://www.openweblog.com/users/hexmode/512973.html). Choose one of the two solutions and run it in the terminal. I had better luck with the second option. It seems to get along better with pulse.

If you go with the first solution, you'll need to run:
```
sudo apt-get install sox libsox-fmt-all
```
to get sox and the file formats you need.


The part of the code that looks like:
```
0,15,30,45 * * * *
```
defines how often the time is read. Right now it will tell you every 15 minutes. You can change this by messing with the numbers. The easiest way to figure out how to do this would be to use the calculator at [http://www.csgnetwork.com/crongen.html](http://www.csgnetwork.com/crongen.html). Don't worry about the part that says "Include the path to your job". Click calculate and you'll have the string you need to replace the above with.


If you get tired of this, run "crontab -r" at the terminal. I'm assuming here you haven't added any cron jobs of your own, as this removes them all. Just to be sure, run "crontab -l" before you start this process and make sure the file is empty. If not, make a backup by running "crontab -l > cron.backup". You can restore this file later by running "crontab cron.backup". This process could be automated quite easily with a script.

Hope this helps!

---

### Post by helwitch on 2008-10-18
I hadn't seen there was a saytime program in the repos. I just ran ```
sudo apt-get install saytime sox libsox-fmt-all
``` and it works fine! Now I've just gotta read the man for cron and figure out how cron works, so I can set it up to run every 15 min between noon and midnight.

---

### Post by forger on 2008-10-18
you have a gui, [gnome-schedule]("apt://gnome-schedule") if it helps

---

### Post by kartoshka on 2008-10-19
If saytime is working for you, try in the terminal:

```
(echo "0,15,30,45 12-23 * * * saytime";echo "0 0 * * * saytime")|crontab -
```

Should give you every 15 min from noon to midnight.

The problem I see with saytime (though I didn't test it personally) is that it doesn't use pulseaudio. So if you're using any other applications with sound, I don't believe you'll hear the time.

---

### Post by forger on 2008-10-19
You're right kartoshka, I tested it and it doesn't work unfortunately with pulseaudio

---

### Post by kartoshka on 2008-10-19
Just realized the first post was about kubuntu, which doesn't use pulseaudio IIRC.

For Ubuntu

```
saytime -f %P%l%M -c | padsp sox -t ul - -t ossdsp /dev/dsp

```

seems to work fine.

---

### Post by rbolio on 2008-10-20
> **kartoshka said:**
> Just realized the first post was about kubuntu, which doesn't use pulseaudio IIRC.

For Ubuntu

```
saytime -f %P%l%M -c | padsp sox -t ul - -t ossdsp /dev/dsp

```

seems to work fine.

Could you please explain this to noobs like me?

---

### Post by rbolio on 2008-10-20
wait! raincheck.... i wrote a simple tutorial from what i have found on the net.... just waiting for it to be aproved... (pwnd)  its really simple...ill post link as soon as i can.

---

### Post by kartoshka on 2008-10-21
The "-f %P%l%M" formats the output of saytime. There are a couple other options. Manpages are your friend :). The -c flag is to send the output of saytime to stdout.

The "|" symbol is the pipe redirect. It takes whatever is sent to stdout and redirects it as input to the next program in the command. Google "i/o redirection" to find out more about this.

The next part of the command is a bit more complex. "padsp" is a part of the pulseaudio server that serves as a wrapper for programs that use oss but don't support pulse. So we need this to avoid conflicts with other applications that might be using the sound card at the same time saytime tries to run.

"sox" is a program to do alot of things with audio files (man sox to find out exactly what). Here it's being used to convert the output of saytime on the fly and send the resulting stream to the sound card. "-t ul -" tells sox to get its input from stdin (piped from saytime) in the ul (uLAW - compressed wav) format. "-t ossdsp /dev/dsp" tells sox to reformat the stream and output to /dev/dsp (essentially the sound card).

Hopefully this clears things up a bit.

---

