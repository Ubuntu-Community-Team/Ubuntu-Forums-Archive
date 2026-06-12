---
title: "TightVNC Viewer - copy/paste function"
date: 2008-07-30
forum: General Help
---

### Post by satimis on 2008-07-30
Hi folks,


Is there a way to highlight/copy text on TightVNCViewer window and paste the text on local PC.  TIA


B.R.
satimis

---

### Post by fragos on 2008-07-30
The simple answer is no, each machine has it's own un-networked paste buffer. You can however paste to a text file and transfer that file. I use NFS to network my machines which makes transferring the text file easy. You might also paste to a file on the web which can be read from the target machine.

---

### Post by satimis on 2008-07-30
> **fragos said:**
> The simple answer is no, each machine has it's own un-networked paste buffer. You can however paste to a text file and transfer that file. I use NFS to network my machines which makes transferring the text file easy. You might also paste to a file on the web which can be read from the target machine.
Hi fragos,


Thanks for your advice.


I'm remotely installing and configuring the OS running as guest on a virtural machine.  Both the OS and the virtual machine, the host, are headless servers without X packages installed.  I need to copy the config steps and output on file for reference.  That is what I expect to do. There is no browser running on the guest.  


Years ago I applied a method echo the steps performed and their output on a file.  All data can be added in sequence.  I can't recall exactly how to do it.  It was a simple Unix command.  The recording can be stopped and resumed.  I think this will be the only way to achieve my goal.  Thereafter I can transfer the file to a storage place.


I'll start googling around and post another thread for advice.


B.R.
satimis

---

### Post by 3rods on 2008-07-30
You can just use putty for this. 

Start putty, second item down on the left is "logging", pick that and choose "all session output" then choose the file location under it. Log on to your server cat the file and viola - the terminal output is sent to the txt file where you told putty. 

Getting it back in is just as easy. Copy it in your OS, then vim or vi the file
```
vim apache.conf
```
then you just hit **i** to begin editing in vim, then right click in the terminal. Putty will spit out the text as input.

[http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html]("http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html")


Sorry, I was assuming your host OS was windows. Is it?

---

### Post by fragos on 2008-07-30
> **satimis said:**
> Hi fragos,


Thanks for your advice.


I'm remotely installing and configuring the OS running as guest on a virtural machine.  Both the OS and the virtual machine, the host, are headless servers without X packages installed.  I need to copy the config steps and output on file for reference.  That is what I expect to do. There is no browser running on the guest.  


Years ago I applied a method echo the steps performed and their output on a file.  All data can be added in sequence.  I can't recall exactly how to do it.  It was a simple Unix command.  The recording can be stopped and resumed.  I think this will be the only way to achieve my goal.  Thereafter I can transfer the file to a storage place.


I'll start googling around and post another thread for advice.


B.R.
satimis

"> file.txt" added to a command with terminal output writes the output to "file.txt"

---

### Post by 3rods on 2008-07-30
I must have misunderstood. I thought you wanted to transfer text from one server to the other - for, like, copying config files and what not. 

If you want to record and replay, try this:
```
http://linux.byexamples.com/archives/279/record-the-terminal-session-and-replay-later/
```

---

### Post by satimis on 2008-07-30
> **fragos said:**
> "> file.txt" added to a command with terminal output writes the output to "file.txt"
Hi fragos,


I tried following steps on terminal;

$ ps aux | grep mysql > /path/to/test.txt
$ ls -al >> /path/to/test.txt

etc.

The output were recorded on the file in sequence but without the commands.  Beside I can't read the output on terminal.  It would be difficult for me to config the OS.


B.R.
satimis

---

### Post by 3rods on 2008-07-30
Both of my solutions will accomplish what you are trying to do. Use putty if you're running Windows or use script command if you're using *nix. 

What OS are you using?

---

### Post by fragos on 2008-07-31
If what you want is the commands and not the output you could try writing shell scripts to use on both machines. Shell scripts also allow the passing of parameters to allow some variability.

---

### Post by satimis on 2008-07-31
> **3rods said:**
> I must have misunderstood. I thought you wanted to transfer text from one server to the other - for, like, copying config files and what not. 

If you want to record and replay, try this:
```
http://linux.byexamples.com/archives/279/record-the-terminal-session-and-replay-later/
```
Hi 3rods,


Thanks for your link.

I have the script file download on /home/satimis/ and renamed it rec_script.sh.  "chmod +x" it making it executable.


I read following links;

[http://linux.byexamples.com/archives/279/record-the-terminal-session-and-replay-later/](http://linux.byexamples.com/archives/279/record-the-terminal-session-and-replay-later/)
and
[http://www.linuxinsight.com/replaying-terminal-sessions-with-scriptreplay.html](http://www.linuxinsight.com/replaying-terminal-sessions-with-scriptreplay.html)


But can' figure out how to play it.


On terminal;

$ /home/satimis/rec_script.sh -t 2> tutorial.timing -a tutorial.session

What are 2 and tutorial.timing for ?


Any idea?  TIA


B.R.
satimis

---

### Post by satimis on 2008-07-31
> **fragos said:**
> If what you want is the commands and not the output you could try writing shell scripts to use on both machines. Shell scripts also allow the passing of parameters to allow some variability.
Hi fragos,


I need to have both commands and outputs on the file as well as on the terminal.  The latter allows me to perform configuration.  Otherwise I will work blindly.


B.R.
satimis

---

### Post by satimis on 2008-07-31
> **3rods said:**
> Both of my solutions will accomplish what you are trying to do. Use putty if you're running Windows or use script command if you're using *nix. 

What OS are you using?
Hi 3rods,


I'm running Ubuntu as OS on the server.


The script recalls me what I did several years ago.  There was an Unix command similar to the script.  I can start/stop it.  The commands and their output were displayed on terminal and recorded on a file simultaneously.


B.R.
satimis

---

### Post by satimis on 2008-07-31
Hi folks,


I have my problem partially solved with Unix tee command.


Tried tee command as follows;

$ ps aux | grep mysql | tee /path/to/output.txt

It displayed the command and its output on console but only saved the output on output.txt without the command executed.


2)
$ ls -l | tee -a /path/to/outpu.txt

The output was added to the file also without the command.


3)
$ locate test.txt | tee -a /path/to/output.txt```

locate: warning: database `/var/cache/locate/locatedb' is more than 8
days old
```

It won't add the warning on the file.


My remaining problem pending for a solution is as follows;

1) to save the command executed on output file
2) to save warning on output file


B.R.
satimis

---

### Post by satimis on 2008-07-31
Hi folks,


Linux script command solves my problem.

$ script /path/to/output.txt

$ run other commands

$ exit
save all output including commands on the file.

$ script -a /path/to/output.txt
resume script and continue adding output on the file.


Thanks


Now I do hope there will be no problem to run;

$ scp /path/to/output.txt desktop_LAN_IP:/path/to/directory

exporting the file back to destop PC


B.R.
satimis

---

### Post by 3rods on 2008-07-31
Good, I'm glad that worked for you.

---

### Post by JLalwani on 2011-08-17
I found one way to do this without writing to files

a) Start vncserver on the linux machine
b) Start the vncviewer on your local pc. Connect and Log in
c) Within the VNC window, type in the command xclipboard&. Keep this up in the background as long as you are using the viewer. Might be useful to add it to your startup

Top copy from windows and paste into Linux:
1) On Windows, highlight and copy test
2) Go over to the little xclipboard screen and middle click. Your copied text will appear there
3) Go over to the window you want to paste into and press ctrl-V

To copy from Linux and paste into Windows
1) Copy the text the way you normally copy
2) RIght click on xclipboard. The text will appear there
3) Paste into windows. The text will appear there

By using xclipboard as an intermeditiary, you can transfer the clipboard contents between local and remote machines.

---

