---
title: "unable to run program"
date: 2008-10-31
forum: General Help
---

### Post by Achilles124 on 2008-10-31
I am unable to run the program adept manager. It gives me the following warning:

You will not be able to change your system settings in any way (install, upgrade, remove software), because this application needs special administrator root privileges.Please run it as root or through kdesu or sudo programs to be able to perform these actions

[http://www.flickr.com/photos/11774983@N02/2988831724/sizes/o/]("http://www.flickr.com/photos/11774983@N02/2988831724/sizes/o/")

So I tried to run it in terminal by typing the command:
sudo adept or sudo adept manager.

That didn't work. How to run it?

Thanks beforehand.

---

### Post by lH)4~mK0e on 2008-10-31
If you are looking to install a program from the Ubuntu repositories, the easiest way is to click on Applications, then Add/Remove...

This will give you a list you can choose from and it is organized by application types.  When you choose to install an application, you will automatically be prompted for a password.  This will be the same password you log in with.

Hope this helps.

---

### Post by Achilles124 on 2008-10-31
You don't understand my question, miwarlock002. The program is already installed from the Ubuntu repositories. So that is not the problem.

The problem is that I am not able to run the program although I have installed it the usual way.

---

### Post by lH)4~mK0e on 2008-10-31
My apologies for the misunderstanding.  If it was installed through the normal means, then it could be in your Applications menu under one of the entries that would seem appropriate for the application type.  Otherwise, if you want a quicker method of running an application you have installed, then you can just push the keys Alt and F2 together and type in the same name as the program you have installed (i.e. if you installed firefox, then you would just put the word firefox in the text field) and click Run.

---

### Post by Achilles124 on 2008-10-31
I have used Alt-F2 but that didn't work. The same errormessage.

---

### Post by Jive Turkey on 2008-10-31
Why are you trying to use adept in Gnome?  Adept is KDE, you might not have the dependencies installed to call the sudo rights or something, not sure.  Use Add/Remove or synaptic for that stuff, or use apt-get in the cli.  I'm assuming that you want to use adept to add or remove software right? Your screenshot looks like you are using Gnome/Ubuntu, Adept might be the right tool for the job in Kubuntu, and probably should work in Ubuntu but may be broken in this case.  

I noticed this in the package description for adept, make sure that is installed.
> Please also install libqt-perl if you want the KDE Debconf frontend to function.

Hope that helps.

---

### Post by Achilles124 on 2008-10-31
okay, ty for answering.

---

