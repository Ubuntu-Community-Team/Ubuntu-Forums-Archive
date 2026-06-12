---
title: "Permanently turns off MacbookAir 2011 Mid Keyboard backlit  14.04"
date: 2014-10-15
forum: Hardware
---

### Post by Evan I S on 2014-10-15
Greeting!

Currently I am having an issue with keyboard backlit always turns on at maximum.  With solutions provided by earlier posts, I could find a solution.

This is my current workaround.
following command lines saved onto kbdoff.sh

sudo chmod 777 /sys/class/leds/smc::kbd_backlight/brightness
echo 0 | tee -a /sys/class/leds/smc::kbd_backlight/brightness

It works well!  But!!
in order to execute the scripts I have to go through sudo.  It is troublesome cos I need to run the script at startup and whenever waking up from suspend the keyboard back light comes back.  I have to execute again to turn it off.  As someone suggested strongly get user give root privilege for the commands with sudo visudo.  WIth a string of hope did the following.

In my visudo, below line written

evn ALL=(ALL) NOPASSWD: /home/evn/kbdoff.sh

It supposed to execute the script without prompting sudo passwd if I understood correctly though It does not.  Therefore I still do manually.  I am seeking a rock solid proven solution with step by step approach.  I would appreciate your help! Anyone has idea?
PS I love xbacklight.  Is there any app does same job for keyboard backlight?

Regards,
Evan

---

### Post by matt_symes on 2014-10-19
Hi

> **Evan I S said:**
> Greeting!

Currently I am having an issue with keyboard backlit always turns on at maximum.  With solutions provided by earlier posts, I could find a solution.

This is my current workaround.
following command lines saved onto kbdoff.sh

sudo chmod 777 /sys/class/leds/smc::kbd_backlight/brightness
echo 0 | tee -a /sys/class/leds/smc::kbd_backlight/brightness


(sudo chmod 777 /sys/class/leds/smc::kbd_backlight/brightness). 

Chmoding the sysfs file to world writable permissions to then write to it without elevated privileges is not the way to do it. 

Anybody or any process can then write to the file and the creates a security risk. 

It circumvents Linux's security model and is unnecessary. Please do not do this :)

The way to achieve what you were trying to achieve is to give elevated privileges to the command that actually needs it.

```
echo 0 | **sudo** tee -a /sys/class/leds/smc::kbd_backlight/brightness
```

There is no need for the dangerous and insecure chmod command at all.

BTW: Are you sure you need **tee -a** and not just **tee** ? I don't own one of your keyboards so i cannot check.

> 
It works well!  But!!
in order to execute the scripts I have to go through sudo.  It is troublesome cos I need to run the script at startup and whenever waking up from suspend the keyboard back light comes back.  I have to execute again to turn it off.  As someone suggested strongly get user give root privilege for the commands with sudo visudo.  WIth a string of hope did the following.

In my visudo, below line written

evn ALL=(ALL) NOPASSWD: /home/evn/kbdoff.sh

It supposed to execute the script without prompting sudo passwd if I understood correctly though It does not.  

This is also not a good idea either and also unnecessary :) I would remove the visudo entry.

> 
Therefore I still do manually.  I am seeking a rock solid proven solution with step by step approach.  I would appreciate your help! Anyone has idea?


This is what is would do.

First remove the chmod command from your script (/home/evn/kbdoff.sh) so it just has this in it. No need to use sudo as it will be called by root anyway.

```
echo 0 | tee -a /sys/class/leds/smc::kbd_backlight/brightness
```

Then move the script into /etc

```
sudo mv /home/evn/kbdoff.sh /etc
```

Make root the owner.

```
sudo chown root:root /etc/kbdoff.sh
```

Set the permissions (just in case they are wrong at the moment)

```
sudo chmod 755 /etc/kbdoff.sh
```

Now the script needs to be called. To call the script at start up, add an entry to /etc/rc.local. This will ensure your script gets called at startup and reboot but not at resume or thaw.

```
sudo sed -i '/exit 0/ i\/etc/kbdoff.sh' /etc/rc.local
```

Then reboot your PC, shutdown your PC and restart your PC.

Post back on how that works.

If there are no problems we'll move on to fixing resume and thaw by creating  a symlink in sleep.d (although i need to double check that sleep.d is still the correct place).

Kind regards

---

### Post by Evan I S on 2014-10-20
Before saying anything else, thank you very much for your help.  I've  been trying to use Ubuntu since version 10.04 noticed there is an OS  other than Windows and MacOS.  But made me gaving up many times to use  it because its unbacked wildness to a Windows user often trapped me and  drove me nut whereas Windows did not in finding wifi network and video  cards drivers and run apt-get install command etc.  Now I give it a try  to offer new life to my Macbook Air.  I hope this time I can train this  wild horse to travel with full control.

Back to the issue.  Following lines are what Ive done with terminal.  Rebooted multiple times after that.  

evn@engineered:/etc$ cat kbdoff.sh 
echo 0 | sudo tee /sys/class/leds/smc::kbd_backlight/brightness
evn@engineered:/etc$ sudo chown root:root /etc/kbdoff.sh
evn@engineered:/etc$ sudo chmod 755 /etc/kbdoff.sh
evn@engineered:/etc$ sudo sed -i '/exit 0/ i\/etc/kbdoff.sh' /etc/rc.local
evn@engineered:/etc$ sudo init 6

Unfortunately Issue not resolved..What can I do next?


Regards,
Evan

---

### Post by Bucky Ball on 2014-10-20
Please post a new thread with a descriptive title for the wake up issue. We like to stick to one support issue per thread here. Less confusing. Thanks. ;)

---

### Post by Evan I S on 2014-10-20
Hi Bucky Ball!

You are right I was greedy to get two answers from one thread. To prevent from leading people confuse, I removed the comment on new issue from the previous reply of mine and have posted new thread so that you could reply to the solution.  Thank you! :-)


[B]------> Not waking up from suspend by closing lid Macbook Air 2011
[/B][http://ubuntuforums.org/showthread.php?t=2249258&p=13148113#post13148113](http://ubuntuforums.org/showthread.php?t=2249258&p=13148113#post13148113)

---

### Post by Bucky Ball on 2014-10-20
> **Evan I S said:**
> To prevent from leading people confuse, I removed the comment on new issue from the previous reply of mine and have posted new thread so that you could reply to the solution.  Thank you! :-)




Good plan and thanks. ;)

Feel free to provide a link to that new thread here. Good luck.

---

### Post by matt_symes on 2014-10-22
Hi
> 
evn@engineered:/etc$ cat kbdoff.sh 
echo 0 | **sudo** tee /sys/class/leds/smc::kbd_backlight/brightness

Get rid of the sudo command from kbdoff.sh and make it look like this...

```
echo 0 | tee /sys/class/leds/smc::kbd_backlight/brightness
```

Reboot and post back on efficacy.

Kind regards

---

### Post by Evan I S on 2014-12-01
@matt_symes: Thank you very much for all your helps!!! I dismantled my MBA as there was a feeling of tingle when I touched the trackpad lately.  I put back everything in order then the unpredictable kbd back light issue gone. Furthermore I successfully automate the command to turn off the back light on boot.  Only a change I made was used joe editor instead vi.  I am sure I know how to save in vi  :w! :-)  so it wasn't the issue.  Anyway I am happy with my lovely ubuntu.  Regards, Evan

---

### Post by Bucky Ball on 2014-12-01
Good news. To help others, could you mark the thread as solved, please (see the second link in my signature). This won't close the thread. ;)

Enjoy!

---

