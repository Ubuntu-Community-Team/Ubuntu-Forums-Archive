---
title: "Ubuntu 7.10 having random system failure on Gateway M350WVN (sound issue)"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by fourdegrees on 2008-01-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/182402](https://bugs.launchpad.net/ubuntu/+bug/182402) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I've encountered what I believe is an issue with the sound system. I've searched all over for a similar situation, but haven't come up with anything.

In short, Ubuntu 7.10 on my Gateway M350WVN laptop crashes when playing back audio.

In medium, any type of file with an audio elements plays fine (I get sound from speakers, headphones, volume works, etc.) but I'm getting sporadic crashes while the files are playing. I'm not sure exactly where the problem lies, whether in Ubunutu, GNOME, ALSA, the drivers, the kernel, or something combination. I've spent a lot of time testing to replicate the behavior, which is definitely possible. Unfortunately, this is the probably the most annoying kind of bug. It's intermittent, happens under a wide variety of circumstances, and is "fatal" to the system (complete and total lock).

In long, I've been looking over various troubleshooting and bug reporting guides getting a sense of what information is useful/necessary. Hopefully all of this will help nail down the issue and get it resolved. Here goes:

A.) System Specs

1.) machine: Gateway M350WVN laptop ([http://support.gateway.com/s/Mobile/Gateway/400WVN/3501666sp58.shtml](http://support.gateway.com/s/Mobile/Gateway/400WVN/3501666sp58.shtml))

a.) Audio chipset: Sigmatel 174; Soft Audio AC97 rev 2.3 codec (STAC9752)
b.) Sound support: PCI interface audio, Multi-stream Direct Sound and Direct Sound 3D acceleration, SoundBlaster Pro, MIDI, Windows Sound System compatible, MP3, WMA, PCI Power Management Interface (PPMI) 1.1 compliant
c.) Volume controls: Volume control buttons on front of notebook, Volume control keys on keyboard, Software control provided through Windows
d.) Internal speakers: Stereo speakers built into front of notebook, 2 W maximum output
e.) Audio jacks: Stereo headphone output, Monophonic microphone input

2.) distro: Ubuntu 7.10

a.) Installed from LiveCD
b.) "Fresh" install except for enabling wireless, installing restricted-ubuntu-extras to get wider variety of sound testing options, installing official Macromedia Flash plugin for Firefox
c.) note that I replicated the crash before and after these changes (see below)

3.) kernel: Linux fd-ubuntu-lap 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

4.) See below for files with complete output of commands like lspci, etc.

B.) Symptoms of Crash/Freeze/Lock

1.) sound stops playing, display freezes, no movement of mouse, no response from keyboard
2.) CTRL+ALT+Backspace does nothing
3.) toggling CAPSLOCK does nothing (light doesn't change)
4.) CTRL+ALT+F1 does nothing
5.) ALT+PrntScrn+reisub does nothing
6.) Fn keys, media keys, app buttons do nothing
7.) only way to get system back is to manually power cycle
8.) power cycling results in fsck saying volume not cleanly unmounted, runs a check, repairs, reboots successfully

C.) Replication

1.) crash after random interval during 

a.) rhythmbox - streaming m3u over http
b.) rhythmbox - playing mp3 across ntfs partition
c.) rhythmbox - playing mp3 local to ext2 partition
d.) totem - playing DVD
e.) gxine - playing DVD
f.) login screen - entered correct user/pass, froze while playing login sound
g.) gnome-sound-properties - playing test sound with no other input to system
h.) gnome-sound-properties - playing test sound while changing volume with Fn keys

2.) crash does NOT happen during

a.) any of the above cases while having the sound muted (whether from muting at a certain level, or turning volume all the way down)

D.) Testing

1.) memtest - 4.5 passes, 0 errors detected

2.) gdb backtrace - rhythmbox (local mp3s)

a.) first run - music played without crash for over an hour, but unable to generate report because entire system crashed, not just the application, once system rebooted (gdm) stated their was no data to gather into a report

3.) valgrind - rhythmbox (local mp3s)

a.) first run - system ran exceptionally slow, almost no sound actually made it to the speakers, music appeared to play for 45 minutes without crash, ended test, resulting file was so large I deleted it because the text editor choked a couple times trying to open it
b.) second run - system ran exceptionally slow, no sound came out of speakers, only let test run for a few minutes and manually closed rhythmbox, report successfully generated but obviously couldn't capture a crash event
c.) third run - as above, but locked up after about 3 seconds, no report generated because entire system crashed

4.) strace - rhythmbox (local mp3)

a.) first run - app ran for over an hour without crashing, ended test, strace generate 49.5mb file that choked anything that tried to open it
b.) second run - app crashed after about 10 minutes of play, but the file generated was corrupted during the crash such that I can't get it to open in any text editing program.
c.) third run - app ran for length of song, no crash, ended test, large file generated
d.) fourth run - same as third

5.) strace - gnome-sound-properties playing test sound

a.) 14 runs w/o crash generated log files ranging from 1.7 to 5 MB
b.) 15th run, generated crash, corrupted file, ubunutu reports that .log file is .xml format and shouldn't be trusted, renamed to .xml and opened, contained some random stuff, but didn't resemble an strace log file at all, suggests file was corrupted similar to the one generated with rhythmbox

6.) /var/crash directory is completely empty

E.) Generated Files in M350WVN-ubuntu-testing-files.tar.gz (** marks files not included in archive, available on request)

1.) commands run & their output

a.) uname -a > M350WVN-uname.txt
b.) sudo lspci -vvnn > M350WVN-lspci-vnn.txt
c.) lsmod > M350WVN-lsmod-info.txt
d.) dmesg > M350WVN-[various].log
e.) tail -2 /proc/asound/oss/sndstat > M350WVN-tail-proc-asound-oss-sndstat.txt 
f.) amixer > M350WVN-amixer.txt 
g.) asoundconf list > M350WVN-asoundconf-list.txt
h.) cat /proc/interrupts > M350WVN-proc-interupts.txt
i.) top -b -n3 > M350WVN-top.log
j.) sudo dmidecode > M350WVN-dmidecode.txt

2.) script/program output

a.) M350WVN-alsa-info.txt (./alsa-info.sh)
b.) M350WVN-aadebug-info.log (./aadebug)
c.) M350WVN-gdb-rhythmbox.txt (gdb, generated w/o crash)
d.) M350WVN-valgrind.log.5762 (valgrind, generated w/o crash)
e.) **M350WVN-strace-rhythmbox-01.log (49.6 MB, generated without crash)
f.) M350WVN-strace-rhythmbox-02.log (6.0 MB, generated with crash, opening gives error about encoding detection, file corrupted by crash)
g.) **M350WVN-strace-rhythmbox-03.log (17.6 MB, generated without crash)
h.) **M350WVN-strace-rhythmbox-04.log (25.2 MB, generated without crash)
i.) **M350WVN-strace-test-snd01.log - M350WVN-strace-test-snd14.log (all 14 files generated without crash)
j.) M350WVN-strace-test-snd14.log (322 bytes, generated with crash, opening gives warning that file is actually .xml, renaming and opening shows minimal information that does not resemble strace output at all, file presumed corrupted by crash just like the rhythmbox strace above)

3.) images (hosted by imageshack.us, sorry for poor quality, some were spliced together from cell phone pics)

a.) screen photo of crash with top running ([http://img339.imageshack.us/my.php?image=crash01screenbm2.jpg](http://img339.imageshack.us/my.php?image=crash01screenbm2.jpg))
b.) resulting fsck photo ([http://img201.imageshack.us/my.php?image=crash01fsckue7.jpg](http://img201.imageshack.us/my.php?image=crash01fsckue7.jpg))
c.) fsck screen photo after test sound crashing without strace running ([http://img174.imageshack.us/my.php?image=m350wvntestsndcrashfsckzl3.jpg](http://img174.imageshack.us/my.php?image=m350wvntestsndcrashfsckzl3.jpg))
d.) fsck screen photo after crashing during M350WVN-strace-test-snd15.log ([http://img244.imageshack.us/my.php?image=m350wvntestsndcrashfsckna4.jpg](http://img244.imageshack.us/my.php?image=m350wvntestsndcrashfsckna4.jpg))

F.) Listings (concurrently posted and watched at)

1.) [http://ubuntuforums.org/showthread.php?t=665776](http://ubuntuforums.org/showthread.php?t=665776)
2.) [https://bugs.launchpad.net/ubuntu/+bug/182402](https://bugs.launchpad.net/ubuntu/+bug/182402)
3.) [https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3702](https://bugtrack.alsa-project.org/alsa-bug/view.php?id=3702)
4.) [http://bugzilla.kernel.org/show_bug.cgi?id=9742](http://bugzilla.kernel.org/show_bug.cgi?id=9742)

---

