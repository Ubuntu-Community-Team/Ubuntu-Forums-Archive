---
title: "Internal Speakers not working in Ubuntu 20.04 on Pavilion All-In-One 27 - Xa0031ns"
date: 2020-05-14
forum: Hardware
---

### Post by felipeperucho on 2020-05-14
In a fresh install of Ubuntu 20.04 internal speakers does not work: they just crackle a bit when sound is played, and nothing more. Speakers are internal and Bang and Olufsen. Headphones does work properly. I have tried jack retasking, but I have not enough knowledge to find the good way to fix the issue. Any clue?

I varely understand the information above these lines, but maybe its useful to give me a clue to continue my search for a solution:

> cat /proc/asound/cards
 0 [PCH            ]: HDA-Intel - HDA Intel PCH
                      HDA Intel PCH at 0xa4510000 irq 140

> cat /proc/asound/car*/co* |  grep Codec
Codec: Realtek ALC225
Codec: Intel Kabylake HDMI

> lspci -nn|egrep 'ultimedia|udio|sound|AC97|ac97|EMU'
00:1f.3 Audio device [0403]: Intel Corporation Cannon Lake PCH cAVS [8086:a348] (rev 10)

Update: I've found this thread ([https://askubuntu.com/questions/1200906/sound-ubuntu-linux-19-10-on-hp-pavilion-aio-not-working?noredirect=1#comment2013771_1200906](https://askubuntu.com/questions/1200906/sound-ubuntu-linux-19-10-on-hp-pavilion-aio-not-working?noredirect=1#comment2013771_1200906)) with someone with a similar problem that founded that sound works properly after computer goes to sleep mode... Mistery increases :)


Thank you for your time

---

### Post by felipeperucho on 2020-05-15
Solution founded here: [https://askubuntu.com/questions/1200906/sound-ubuntu-linux-19-10-on-hp-pavilion-aio-not-working?noredirect=1#comment2013771_1200906](https://askubuntu.com/questions/1200906/sound-ubuntu-linux-19-10-on-hp-pavilion-aio-not-working?noredirect=1#comment2013771_1200906)

This is what the user vokke says there, summarised:

> Just add 2 lines at the end of /etc/modprobe.d/blacklist.conf:

#fix for hp-pavilion aio 27 xa0013ng
blacklist snd_hda_codec_realtek

Sound is working without any cracks - after returning from sleep mode AND after a cold start! I tested it with Kernel 5.3.0-46-generic #38-Ubuntu SMP

Commands to do this for absolute newcomers:

1. Open a terminal

2. Copy and paste in the terminal, and enter, the following command. It will open notebook program (Gedit) so you can edit the file "blacklist.conf" with administration privileges: 

> sudo gedit /etc/modprobe.d/blacklist.conf

3. Copy and paste at the end of that document ("blacklist.conf") the following lines. The first one does nothing, because has a # at the beginning; its a comment for humans. The next one does the magic. I think that prevents the system to load a problematic codec... or something. It does the magic, as I said:

> #fix for hp-pavilion aio 27 xa0013ng
blacklist snd_hda_codec_realtek

4. Save, reboot and enjoy :)

---

### Post by mishamtrop on 2020-07-01
Hi, I had the exact same issues and resolved it the same way. It mysteriously broke again recently, possibly after a system update. 
Did you have a similar experience?

---

