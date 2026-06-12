---
title: "Clicking noise from Speakers after upgrade"
date: 2009-11-02
forum: Installation &amp; Upgrades
---

### Post by rocklinks on 2009-11-02
Hi guys,

I have upgraded to version 9.10 but unfortunatly have a very strange random clicking noise from my laptop. I'm 95% sure that the click is coming from the built in speakers. However turning the volume down or turning them off completley does not stop the clicking. Any ideas would be greatly appreciated!

Thanks

Craig

---

### Post by barthel on 2009-11-02
By any chance do you have Intel HDA audio? If so, you've encountered a bug related to the power_save parameter. [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/381201]("https://bugs.launchpad.net/ubuntu/+s...ux/+bug/381201")

See my post [here]("http://ubuntuforums.org/showthread.php?p=8203937#poststop").

---

### Post by rocklinks on 2009-11-02
Hey thanks!

I have had a look at the links, but im not sure how to fix the problem? im relatively new to ubuntu.

---

### Post by barthel on 2009-11-04
Sorry for the delay in replying--I was working all day yesterday as an election official (05:00-20:00)--long day.

Here are the steps in excruciating detail.

First, open a terminal window. Click on the menu Applications -> Accessories -> terminal.

Now let's see what your audio card is. In the terminal window, type
```
lspci | grep -i audio
```

In my case, the result is:
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

The key words are "Intel" and "High Definition Audio", also known as HDA.

To see the current setting of the power_save parameter, type:
```
cat /sys/module/snd_hda_intel/parameters/power_save
```
You should see '10', which is the default value.

To turn off the clicking immediately, you must become root. (Normally you would simply use `sudo` to execute a single command as root. In this case, however, sudo will fail. You must perform this command from a root prompt.) In the terminal type
```
sudo su
echo 0 > /sys/module/snd_hda_intel/parameters/power_save

```
This should turn the popping and clicking off. You can verify the setting with the 'cat' command above--the result should now be '0'.

The currently suggested workaround is to have this set in the modules configuration file, however this does not work for everyone. While still at the root prompt, type
```

cd /etc/modprobe.d/
cp -a alsa-base.conf alsa-base.conf.ori
gedit alsa-base.conf

```
This makes a backup copy of your alsa-base.conf file and opens it in an editor.

In the editor, scroll to the bottom. The last line should be:
options snd-hda-intel power_save=10 power_save_controller=N

Highlight and copy that line. Then paste it immediately below itself. We'll comment out the original as a backup and show our changes in the next line. Your end result should look like this for the bottom two lines:
```
#options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel power_save=0 power_save_controller=N
```

Personally, I like to add a comment which dates the change and explains it. So I have something like this:
```
#091031-BaP: Turn off power_save to eliminate annoying pops
#options snd-hda-intel power_save=10 power_save_controller=N
options snd-hda-intel power_save=0 power_save_controller=N
```

Save the modified file and exit gedit. In the terminal window, type 'exit' to leave the root shell.

The next time you reboot, the popping should disappear. If it doesn't, just do this in a terminal each time you boot (until the problem is fixed in an update:
```
sudo su
echo 0 > /sys/module/snd_hda_intel/parameters/power_save
exit

```

I hope this is clear enough for you as an Ubuntu novice. If not, I'll be happy to explain further.

I should add one last word of [COLOR="Red"]WARNING[/COLOR]: While doing this, I had you obtain a root prompt as a necessary part of the process, then continued using the root prompt as a convenience (to eliminate multiple 'sudo's). For new users, the root prompt can be a dangerous thing. (It's still a dangerous thing for old hands, but we "should know better".)  You should always be extremely cautious when running any command as root--if you don't understand what the command does, check its man page. If that's still unclear, don't run the command until you can get further help via Google, the forums, or a local guru.

From a strict security standpoint, you should not trust my advice until you see for yourself what that advice will do. (*I* know I have no evil intentions toward you or your system, but you don't know that. The most common scenario, however, is that I might have made a mistake.) On the positive side, I did show you how to make a backup of the file we changed. I also had you make a backup of the line we changed within the file. These are examples of "Best Practices" that will help you undo any unintended effects of a command.

(Okay, so that was more than one last word... ;) )

Good luck!

---

### Post by rocklinks on 2009-11-04
Thanks alot for that great walkthrough!

Unfortunatly it didn't work :(

However the adding the code everytime  i boot does seem to work touch wood. I will keep you posted if it happens again!

Thanks again friend!

Craig

---

### Post by dryicebomb on 2009-11-13
This did work for me, thanks for the great post.

---

### Post by nehalia on 2009-11-23
[http://ubuntuforums.org/showthread.php?p=8373420#post8373420](http://ubuntuforums.org/showthread.php?p=8373420#post8373420)
 
What if you are getting the clicking noises only when sound is trying to play, and your sound is not Intel HD? (see above link for more details on my problem.)

---

### Post by barthel on 2009-11-24
After the reboot for yesterday's kernel upgrade I decided I was tired of manually resetting this. I've added the line to /etc/rc.local

---

