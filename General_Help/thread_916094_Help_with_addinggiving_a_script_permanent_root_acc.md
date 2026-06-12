---
title: "Help with adding/giving a script permanent root access"
date: 2008-09-10
forum: General Help
---

### Post by jbreezy on 2008-09-10
Is there a way to add, or give a script permanent root permission?  The script I have asks me for my users password every time that I run it. I'd like to be able to simply click on the link to the script and have it display the results without asking for my password.

It's a simple script to check the load cycle count on my laptops hard drive then display the results in gedit.

Here's the script>

#!/bin/bash
echo `sudo smartctl -a /dev/sda | grep Load_Cycle_Count` " | " `date` >> load_count

cp -u load_count /mnt/docs/Docs/updates

gedit load_count

<end script

Anybody have any suggestions?

ty

Running Ubuntu 8.04.1, Gnome 2.22.3, kernel 2.6.24-19

---

### Post by unutbu on 2008-09-10
To run commands as root without password: edit /etc/sudoers:
```
Cmnd_Alias JBREEZYCMD=/home/jbreezy/bin/load_cycles.sh
jbreezy ALL=NOPASSWD: JBREEZYCMD
```

Change "/home/jbreezy/bin/load_cycles.sh" to the correct path for your script. Change jbreezy to your real username.

You can then take the "sudo" out of your script, and make a launcher whose command starts with sudo.

Alternatively, you can add /usr/sbin/smartctl to JBREEZYCMD in /etc/sudoers. 

See [http://ubuntuforums.org/showpost.php?p=5595798&postcount=15](http://ubuntuforums.org/showpost.php?p=5595798&postcount=15)

---

### Post by jbreezy on 2008-09-10
Thanks unutbu, that's exactly what I've been looking for. Worked like a charm.

I tried sudo visudo to edit my sudoers file but didn't enter in the right bit of info. Works like a charm now.

---

### Post by jbreezy on 2008-09-10
Okay, hopefully someone will find this info useful.

I used to keep hearing my hard drive make a "clicking" sound every so often and only noticed it when I was running Ubuntu. SuSE and Vista did not seem to make my hard drive click.

So this is how to make a quick script that will check your computers hard drive load cycle count and display the information with gedit.

Note: you will need smartmontools installed
  $ sudo apt-get install smartmontools

1. Create a script named hddloadcount.sh and place it in your home folder.

2. Add this code to the script and save

```
#!/bin/bash

echo 'smartctl -a /dev/sda | grep Load_Cycle_Count` " | " `date` >> load_count

gedit load_count
```

3. Create a custom launcher in one of your panels to link to the hddloadcount.sh script
Right click panel > add to panel > custom application launcher > add
Now select "application in terminal." Type in the "command" box: sudo /home/yourusername/hddloadcount.sh and choose a custom icon if desired.

4. Edit /etc/sudoers to give the script root permissions
$ sudo visudo
And add this to the bottom of the sudoers file, changing JBREEZY with your user name.

```
Cmnd_Alias JBREEZYCMD=/home/jbreezy/bin/load_cycles.sh
jbreezy ALL=NOPASSWD: JBREEZYCMD
```
Save and exit the sudoers file

5. Done. Now when you click your new launcher it will display your hard drives load cycle count. Hope this helps.

---

