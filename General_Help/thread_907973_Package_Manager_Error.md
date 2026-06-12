---
title: "Package Manager Error"
date: 2008-09-02
forum: General Help
---

### Post by maverickzzz on 2008-09-02
Hi,
recently i've got a problem with my update process. Then a friend of mine told me to run these commands:
----------------------------------------------------------------------------------------
sudo rm /etc/apt/sources.list.d/medibuntu.list
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
----------------------------------------------------------------------------------------


after i run those commands, an error sign occured. It says:
----------------------------------------------------------------------------------------
Could not initialize the package information
A unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:Type '--12:23:16--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list, E:The list of sources could not be read.'
----------------------------------------------------------------------------------------


Here's the content of medibuntu.list:
----------------------------------------------------------------------------------------
--12:23:16--  [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list)
           => `hardy.list.1'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.110
Connecting to [www.medibuntu.org|87.98.242.110|:80](www.medibuntu.org|87.98.242.110|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: 226 [text/plain]

    0K                                                       100%   21.33 MB/s

12:23:17 (21.33 MB/s) - `hardy.list.1' saved [226/226]
----------------------------------------------------------------------------------------


Any solutions? Thanks in advance...

---

### Post by baggins on 2008-09-02
When running your command (copied it directly) I get this in my output file.
```
## Medibuntu - Ubuntu 8.04 LTS "hardy heron"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ hardy free non-free
#deb-src http://packages.medibuntu.org/ hardy free non-free

```
Which is corect try doing it again, or get the commands directly from:
[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

-- Jon

---

### Post by iaculallad on 2008-09-02
On your terminal:

Open the medibuntu.list file for editing:

```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```

Select all the texts inside the file and delete it. Save and Close the file.

Back in your terminal, add the Medibuntu repository:

```
sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list

```
Add the GPG key:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

HTH.

---

### Post by maverickzzz on 2008-09-02
Wow... It's working now...
Thanks for the quick replies...

One more thing. I did a few update on the OS itself...
Now, when booting, the screen will show up several version of the OS.
Is there any way to remove the previous version from the list? I mean just delete the unnecessary version from the list and just keep the newest one...

Thanks in advance...

---

### Post by drs305 on 2008-09-02
> **maverickzzz said:**
> One more thing. I did a few update on the OS itself...
Now, when booting, the screen will show up several version of the OS.
Is there any way to remove the previous version from the list? I mean just delete the unnecessary version from the list and just keep the newest one...

Check out the link in my signature line about StartUp-Manager. It will explain why it is doing that, how to correct it, and give some other useful tweaks to the grub menu. StartUp-Manger allows safe and easy editing of menu.lst without opening the file and manually editing it.

---

