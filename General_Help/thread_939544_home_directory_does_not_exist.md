---
title: "home directory does not exist?"
date: 2008-10-06
forum: General Help
---

### Post by HHelsinger on 2008-10-06
After running Remastersys I have lost access to my home/user directory.
On booting I first get a message that "Your home directory is listed as: '/home/howard but it does not appear to exist. Do you want to log in with the /(root)/ directory as your home directory.  It is unlikely that anything will work unless you use a failsafe login."

When I continue, I get the message that "User's $Home/.dmrc file is being ignored....."

The /home directory still shows the guest directory, but my user directory doesn't appear.  

I have seen the posts that propose a sequence of commands:
sudo chmod 644 .dmrc
sudo chown howard .dmrc
sudo chmod 755 /home/howard
such chown howard /home/howard

I have tried that but I think I do not know where and when to enter those commands.   

I can drop into a failsafe terminal.
From there I can get to howard@howard-desktop
I can list the directories.  The home directory shows the Guest directory, which has a .dmrc file.
But there is no howard [my user name] directory.  
When I enter the command "sudo chmod 644 /home/howard/.dmrc" I am told there is no such file.
Can I create one?  How would I do that? how would I do that in a directory that doesn't exist?

Help will be appreciated, as I have lost files needed almost immediately.

thanks.

---

### Post by cariboo on 2008-10-06
You could create a new directory to see if that will work.

If your are in a desktop hit Ctrl-ALt-F1, this will bring you to a command prompt, at the prompt type:

```
sudo mkdir /home/howard
```

THen you can try:

> sudo chmod 755 /home/howard
such chown howard /home/howard

You should now restart, to do this at the prompt type:

```
sudo reboot
```

When you log in after the reboot Ubuntu should recreate most of the configuration files and you should be good to go.

Jim

---

### Post by HHelsinger on 2008-10-06
Thanks, but that got me a new desktop, not my former desktop.   Most importantly, it didn't get me access to any of my documents which were all in the /documents folder under home/howard.

Now I have a new directory home/howard,   but the home/howard/documents folder has nothing in it, being a new folder in a new desktop.  

Similarly there were folders for photos, and pictures, all of which have disappeared.

I can switch user to the Guest directory, as before -- passwords and appearance are all unchanged.  

I hope that by creating a new (but obviously different) home/howard folder I haven't made it more difficult to retrieve the files that should be in that folder.

Any further ideas?  Anyone?

---

