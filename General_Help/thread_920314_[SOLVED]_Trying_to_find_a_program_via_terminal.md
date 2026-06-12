---
title: "[SOLVED] Trying to find a program via terminal"
date: 2008-09-15
forum: General Help
---

### Post by zombrax on 2008-09-15
hey guys,

Just a quick question... 

how do you find a program via the terminal if you know say part of what it is called or find the exact name of the dl file name?

eg. If i wanted to dl say pidgin ... how do i find the exact dl name so that i can use this command.. if i dint know the whole name of the program, like how can i get the terminal to give me a list of closely matched names?

Hope I'm making sense guys! Many thanks in advance.

```
sudo apt-get install <<blah>>
```

---

### Post by devosion on 2008-09-15
This is how you would do it through aptitude.

> sudo aptitude search -your descriptor here-

---

### Post by aloshbennett on 2008-09-15
To add to the above post, you could find additional info about a package by using
> apt-cache show <<blah>>
btw, no need to sudo while using apt-cache :-)

---

### Post by Bizurke on 2008-09-15
you can use *apt-cache search* for finding packages that available. If the amount of results is rather high try putting the search term in quotes to get a more exact result. 

As far as finding stuff once you have it on your system I would try *whereis* and *locate*.

---

### Post by zombrax on 2008-09-15
thanks.. but the it does nothing as in i did this 

```
sudo aptitude search pidgin
```

but it does something for a little while and just gives me back my prompt.. what does this mena? How can i get it to show me whats available to download?

thanks once again

---

### Post by zombrax on 2008-09-15
hmm.. there must be another way to find out what the package is called if i say have the first few letters of it.. like for eg.. if i'm looking for pidgin; can i type in pid in short?

zombrax@ub-lap:~$ apt-cache show pigdin
W: Unable to locate package pigdin
E: No packages found
zombrax@ub-lap:~$ apt-cache show pidgin
W: Unable to locate package pidgin
E: No packages found
zombrax@ub-lap:~$

---

### Post by northern lights on 2008-09-15
```
pille@jox:~$ aptitude search pidgin
i   pidgin                          - graphical multi-protocol instant messaging
p   pidgin-audacious                - pidgin integration with Audacious         
p   pidgin-blinklight               - Blinks your ThinkPad's ThinkLight upon new
i   pidgin-data                     - multi-protocol instant messaging client - 
p   pidgin-dbg                      - Debugging symbols for Pidgin              
p   pidgin-dev                      - multi-protocol instant messaging client - 
p   pidgin-encryption               - pidgin plugin that provides transparent en
p   pidgin-extprefs                 - extended preferences plugin for the instan
p   pidgin-festival                 - pidgin plugin to hear incoming messages us
p   pidgin-guifications             - toaster popups for pidgin                 
p   pidgin-hotkeys                  - Configurable global hotkeys for pidgin    
p   pidgin-libnotify                - display notification bubbles in pidgin    
p   pidgin-librvp                   - MS Exchange RVP instant messaging plugin f
p   pidgin-mpris                    - sets your available message to your curren
p   pidgin-musictracker             - Plugin for Pidgin which displays the curre
i   pidgin-otr                      - Off-the-Record Messaging plugin for pidgin
p   pidgin-plugin-pack              - 30 useful plugins for pidgin              
p   pidgin-sipe                     - Pidgin plugin for connect to LCS          
p   pidgin-themes                   - Smiley themes collection for pidgin   
```

[http://packages.ubuntu.com/search?keywords=pidgin&searchon=names&suite=hardy&section=all]("http://packages.ubuntu.com/search?keywords=pidgin&searchon=names&suite=hardy&section=all")

Pidgin is in the universe repositories. Do you have those enabled (System > Administration > Software Sources)?

---

### Post by cdtech on 2008-09-15
The only thing I know of that uses partial naming would be the "tab completion". This can be enabled via the "/etc/bash.bashrc" file. Uncomment the line:
```
#if [ -f /etc/bash_completion ]; then
# . /etc/bash_completion
#fi
```
This will only complete the names of files and directories using the TAB key.

If you want to know if a package is installed just look in the "Synaptic Package Manager" or create a file of installed packages via:
```
dpkg --get-selections > ~/selections 
```

---

### Post by 3rdalbum on 2008-09-15
Tab completion comes turned on by default.

```
sudo apt-get install pid
```
press tab and the machine beeps because there are multiple ways to complete it. Press Tab again and the possibilities get displayed.

Tab completion also works when looking up man pages and when using the apt-cache "show" and "search" commands. As well as for file paths and running programs.

---

### Post by cdtech on 2008-09-15
Thank you 3rdalbum, wasn't really sure.

---

### Post by Vivaldi Gloria on 2008-09-15
> **zombrax said:**
> hmm.. there must be another way to find out what the package is called if i say have the first few letters of it.. like for eg.. if i'm looking for pidgin; can i type in pid in short?

zombrax@ub-lap:~$ apt-cache show pigdin
W: Unable to locate package pigdin
E: No packages found
zombrax@ub-lap:~$ apt-cache show pidgin
W: Unable to locate package pidgin
E: No packages found
zombrax@ub-lap:~$

It's called pidgin, not pigdin as your commands show. You can search with one of

```
apt-cache search pidgin
apt-cache search -n pidgin
```

Here -n is for searching only in the name. You can get info on the package using one of the commands

```
apt-cache show pidgin
apt-cache showpkg pidgin
apt-cache policy pidgin
```

I suggest you read

```
man apt-cache
```

---

### Post by zombrax on 2008-09-15
ok finally i "think" i have figured out what the problem is.... is there a Pidgin for Feisty?

I have searched for it on all of these.. [[feisty]("http://packages.ubuntu.com/search?suite=feisty&searchon=names&keywords=pidgin")] 	  	 	[feisty-updates] 	  	 	[[feisty-backports]("http://packages.ubuntu.com/search?suite=feisty-backports&searchon=names&keywords=pidgin")]

Could it be ONLY for hardy/gutsy versions? Sorry noob in development :)

---

### Post by Denestria on 2008-09-16
It was probably still called gaim in Feisty.

---

### Post by northern lights on 2008-09-16
It was indeed.

[http://packages.ubuntu.com/search?keywords=gaim&searchon=names&suite=feisty&section=all]("http://packages.ubuntu.com/search?keywords=gaim&searchon=names&suite=feisty&section=all")

---

### Post by zombrax on 2008-09-16
yup many thanks fellas :)

---

