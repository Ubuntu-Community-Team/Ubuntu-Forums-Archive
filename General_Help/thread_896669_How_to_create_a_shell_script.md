---
title: "How to create a shell script?"
date: 2008-08-21
forum: General Help
---

### Post by kramer65 on 2008-08-21
Hello,

I once had to make a shell script which with the help of you guys worked out perfect. Now I need to make another one which automatically does a chmod on a folder.
So I made a file called chmod_scriptie.sh which contains the following code: 
```
sudo chmod 777 -R /home/ricam/Bureaublad/scriptie
```
Using this in a normal terminal window works perfect. When I click it and run it in a terminal window it does nothing however. It doesn't ask for my password either, which I guess it does need to do.

Does anybody know what is wrong here?

---

### Post by Titan8990 on 2008-08-21
You can't and shouldn't sudo a bash script. Bash scripts that need root privileges need to be ran as root. This typically doesn't cause a problem because many BASH scripts are set up as cron jobs or if you are running the script once you remove the sudo from the script and use sudo when you run it.

In your case you would do: sudo ./chmod_scriptie.sh

Also, bash scripts usually begin with:

#!/usr/bin/bash

although it is not needed in this case.

Edit: It is not a good idea to make an entire home directory executable to everyone. Specifically, the .dmrc file in everyones home folder should not have anything more than read rights to groups and other.

Edit again: looked again and saw you were only making a sub directory of your home folder executable to everyone. Still probably not the best practice but you can disregard the the first edit.

---

### Post by kramer65 on 2008-08-21
The reason why I want to do this is because I want to use the folder in my virtualbox/windows installation. I have to perform this action several times per day on a daily basis, so I thought that I could make my life a little bit easier. Maybe chmod 777 is a bit too much, but with this I know for sure it works, and I don't really care about people reading my thesis which I'm writing (scriptie means thesis in Dutch).

Anyway, thanks for the tip. I tried running the following by pasting it into a terminal window:
```
sudo ./home/ricam/Sjablonen/chmod_scriptie.sh
```
But it says "command not found"

Do you know what's wrong here now?

---

### Post by Titan8990 on 2008-08-21
remove the . at the beginning of your absolute path. A period "." indicates current directory so that would only work if your current directory was /.

Let me try to explain this differently. If you are in say your home directory when you run that command it will look for this directory:

/home/ricam/home/ricam/Sjablonen/chmod_scriptie.sh

You can set up a cron job as root to run that script, say, 5 times a day.

Here is a tutorial for setting up a cron job: [http://ubuntuforums.org/showthread.php?t=102626&highlight=cron](http://ubuntuforums.org/showthread.php?t=102626&highlight=cron)


edit: Also, to set up a cron job as root without unlocking the root account just prefix the cron command with sudo:

```
sudo EDITOR=nano && crontab -e
```

---

### Post by kramer65 on 2008-08-21
I tried running the following as well:
```
sudo /home/ricam/Sjablonen/chmod_scriptie.sh
```
But it doesn't work either. It also says "command not found"

I do not want to set up a cron because it needs to be done when I want to. The situation is this; I come home from the library where I've been working on a windows computer from my usb stick. I come home, drag and drop the folder with all my files to the ubuntu desktop (Bureaublad), and I want to chmod it so that I can immediately use it in my virtualbox/windows installation. This is the reason why it has to be done on my command.

Do you have a solution to the "command not found" message?

---

### Post by Titan8990 on 2008-08-21
When you removed the sudo from the script did accidentally leave some whitespace?

Go ahead and add this to the top of the script:

#!/bin/sh

This is known as a "shebang".

---

### Post by kramer65 on 2008-08-21
I tried it, but still no luck..

I'll tell you how everything is now. The file looks like this:
```
#!/bin/sh
chmod 777 -R /home/ricam/Bureaublad/scriptie
chmod 777 -R /home/ricam/sharer/scriptie
```
without any spaces anywhere (double checked)

It is located in the following folder: /home/ricam/Sjablonen
and it is called: chmod_scriptie.sh

I ran in a terminal window the following command:
```
sudo /home/ricam/Sjablonen/chmod_scriptie.sh
```
which gave me the known message "command not found".

When I run this in a terminal window:
```
sudo chmod 777 -R /home/ricam/Bureaublad/scriptie
```
it works perfectly.

The question remains; what am I doing wrong?

(ps. I really apreciate your help.. :-) )

---

### Post by Vivaldi Gloria on 2008-08-21
> **kramer65 said:**
> The question remains; what am I doing wrong?

Are you sure you are writing "/home/ricam/Sjablonen/chmod_scriptie.sh" correctly? Test:

```
ls -l /home/ricam/Sjablonen/chmod_scriptie.sh
``` 

Also make your script executable.

---

### Post by kramer65 on 2008-08-21
"Also make your script executable."

Grrrrrreat! That was it!! Pretty stupid of me.. :-)

Anyway, that helps a lot! And I learned another thing.. ;-)

---

### Post by Vivaldi Gloria on 2008-08-21
> **kramer65 said:**
> "Also make your script executable."

Grrrrrreat! That was it!! Pretty stupid of me.. :-)

Anyway, that helps a lot! And I learned another thing.. ;-)

Have fun. :-)

---

