---
title: "Printer, Media Player Issues"
date: 2008-10-07
forum: General Help
---

### Post by uzzo2 on 2008-10-07
hello all, i am having a strange problem maybe someone can help me with. lately my media players (rhythmbox, vlc) wouldn't work after opening them when my computer had been running for a while. i could reboot and then open them up and they would work fine, now the printer is doing the same thing. i click to print something, it won't print, reboot and it'll start printing the last job in the queue at the sign in page at bootup. thanks in advance for any advice.

---

### Post by lian1238 on 2008-10-07
Could it be that something is running intensively in the background? For example, indexing? Look at the system monitor for constant high CPU usage or type **top** in the terminal to see if anything is taking up the CPU.

In the case of your printer, it could be that the printer is idling and the driver is unable to make it resume from idle. Just my guess.

Edit: Also, try restarting X (Ctrl+Alt+Backspace) instead of rebooting.

---

### Post by uzzo2 on 2008-10-07
> **lian1238 said:**
> Could it be that something is running intensively in the background? For example, indexing? Look at the system monitor for constant high CPU usage or type **top** in the terminal to see if anything is taking up the CPU.

In the case of your printer, it could be that the printer is idling and the driver is unable to make it resume from idle. Just my guess.

Edit: Also, try restarting X (Ctrl+Alt+Backspace) instead of rebooting.
top - 12:52:34 up  1:02,  2 users,  load average: 0.01, 0.08, 0.13
Tasks: 131 total,   2 running, 129 sleeping,   0 stopped,   0 zombie
Cpu(s):  2.4%us,  1.0%sy,  0.0%ni, 96.7%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%
Mem:   2985768k total,   842676k used,  2143092k free,    22496k buffers
Swap:  8747352k total,        0k used,  8747352k free,   446480k cached

here's what i got from that command in the terminal, that's with rythmbox running and 3 tabs open with firefox, thanks.

---

### Post by lian1238 on 2008-10-07
Did you do this when rhythmbox is not playing? Looks normal.

---

### Post by uzzo2 on 2008-10-07
top - 15:32:46 up 3 min,  2 users,  load average: 0.52, 0.81, 0.37
Tasks: 127 total,   1 running, 126 sleeping,   0 stopped,   0 zombie
Cpu(s):  0.5%us,  0.3%sy,  0.0%ni, 99.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2985768k total,   649368k used,  2336400k free,    16952k buffers
Swap:  8747352k total,        0k used,  8747352k free,   362932k cached

this is without rhythmbox running

---

### Post by lian1238 on 2008-10-07
Could you try that when it doesn't work - after your computer has been running for a while. Don't know if it has anything to do with your screensaver and power management settings. Try turning them off for the moment.
And does it happen for EVERY program? Or mainly the media players and your printer? Next time it happens, try running rhythmbox from the terminal. You might see some informative errors.

---

### Post by uzzo2 on 2008-10-07
> **lian1238 said:**
> Could you try that when it doesn't work - after your computer has been running for a while. Don't know if it has anything to do with your screensaver and power management settings. Try turning them off for the moment.
And does it happen for EVERY program? Or mainly the media players and your printer? Next time it happens, try running rhythmbox from the terminal. You might see some informative errors.

ok lian, thanks a lot, i haven't noticed with anything except for the media players and just recently the printer. as far as the power mgmt settings this has always happened when i am working or just surfing the net, not when it's in the hibernation mode. i actually think i have all that turned off so it just seems to do it if i am using the computer for a while and decide to listen to some tunes. i hate to show my ignorance here, but could you tell me how to run rhythmbox from the terminal and the next time it acts up i'll try that and post it here. it's not really a big deal i guess, just reboot or try the trick you stated earlier with restarting x.  i would just like to find out what is causing it so i can learn something, i am still in the early part of the learning curve with ubuntu. thanks again for the advice

---

### Post by lian1238 on 2008-10-07
> **uzzo2 said:**
> i hate to show my ignorance here, but could you tell me how to run rhythmbox from the terminal and the next time it acts up i'll try that and post it here.
No worries! We're all here to learn. To start rhythmbox from the terminal, just open the terminal: **Applications->Accessories->Terminal**. Then type **rhythmbox** into it. And rhythmbox will "take over" this terminal, so don't close it. When you get that problem again, you can post the errors up here.

You could also open another terminal, and run **top** in it. Let it run while you work. If something goes wrong, look at the %CPU column. If it's 100% or constantly high for no apparent reason, that program could be hanging. You'll see the name under the Command column. To force it to quit, open another terminal (Yup, terminals are your friends ;)) and type **killall** followed by the hanging program. (Eg. **killall rhythmbox**) You can use TAB to auto-complete the command. For example, when firefox is hanging, I type "killall fire<tab>" then it becomes "killall firefox-bin" automatically. Very useful. When nothing appears when you press TAB twice, then there's nothing to kill.

Note: There's a known issue: rhythmbox hangs (100% cpu usage but plays the song till the end) when playing VBR-encoded mp3's. I doubt it's related to your problem, but I have a thread [here]("http://ubuntuforums.org/showthread.php?t=940685"). I can reproduce this everytime.

---

### Post by uzzo2 on 2008-10-07
okay, this was really quick, i got on a news website and tried to play a video, no sound, ctrl/alt/bkspc, played the video. i reopened rythmbox and it froze again, the output from "top":
top - 17:30:45 up  2:01,  3 users,  load average: 0.15, 0.37, 0.24
Tasks: 172 total,   2 running, 170 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.1%us,  0.8%sy,  0.0%ni, 97.8%id,  0.0%wa,  0.3%hi,  0.0%si,  0.0%st
Mem:   2985768k total,  1060376k used,  1925392k free,    26528k buffers
Swap:  8747352k total,        0k used,  8747352k free,   516836k cached

i then closed rythmbox and did what you said to open it from the terminal, same thing, just frozen, the terminal too, no errors.

---

### Post by lian1238 on 2008-10-07
Okay, sounds like an audio problem. When it happens again, try going into System->Preferences->Sounds and test the sound device. Do this when it is NOT happening also. You should here a beeeep. Some application could be grabbing your audio output device all to itself. Happened to me on an older version of Ubuntu.

---

### Post by uzzo2 on 2008-10-07
> **lian1238 said:**
> Okay, sounds like an audio problem. When it happens again, try going into System->Preferences->Sounds and test the sound device. Do this when it is NOT happening also. You should here a beeeep. Some application could be grabbing your audio output device all to itself. Happened to me on an older version of Ubuntu.
looks like you hit the nail on the head so to speak, i ran all the tests in sounds and didn't hear anything.

---

### Post by lian1238 on 2008-10-08
> **uzzo2 said:**
> looks like you hit the nail on the head so to speak, i ran all the tests in sounds and didn't hear anything.

Let's diagnose this thoroughly.

[LIST=1]
[*]Run the test right after startup for each modules listed - you can stick with just the first test (Sound Events); rhythmbox should have no problem now but don't run that yet
[*]Choose the one that works, for the others too - Music and Movies, so on. If none of them works, what are the errors?
[*]Run rhythmbox.
[*]While rhythmbox is playing a song, run the test again if it worked before. Both should be play - the beep and the song.
[/LIST]
If there appears to be a problem with the audio, you could try installing **pulseaudio** if you haven't already. I don't know how to do that as I haven't done it before.

---

### Post by uzzo2 on 2008-10-08
ok, i thought i had found a link; got up this morning and booted up, was letting it warm up while taking my medicine. then i logged in, opened up firefox and went to my webmail page and then came to the forum from the link in my email notice. i opened up sounds after reading your post and still nothing worked. i rebooted, opened up sounds again and all the tests worked except for the sound capture test in audio conferencing. then, i reopened firefox and ran the sound checks again, nada, nothing. closed firefox, ran the checks again and they all worked except for the one listed above. i did this 3 or 4 times consecutively and got the same results so i was beginning to think it was a problem with firefox. i rebooted again, opened up firefox and ran the tests again, they all worked this time except for the sound capture one. so it seems to be an intermittent problem, also did the check with rythmbox running and ran the tests after all of the above and could hear the beep with the music playing. i didn't get any errors errors when the tests weren't working, just the little box that pops up for the test with the little task bar running back and forth but no sound. should i go ahead and install pulseaudio, and if so, is it in synaptic?

---

### Post by lian1238 on 2008-10-08
If you're using Hardy, pulseaudio should be installed.
Check the wiki: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

