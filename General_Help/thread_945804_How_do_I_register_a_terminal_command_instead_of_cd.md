---
title: "How do I register a terminal command instead of cd'ing and using ./app every time?"
date: 2008-10-12
forum: General Help
---

### Post by sstecken on 2008-10-12
I have a file that can be executed with ./app

How do I register it so that every time I want to execute it, I can just bash "app" instead of cd'ing to the directory and then doing a ./app

---

### Post by unutbu on 2008-10-12
Make a directory to put your executables. Let's say, ~/bin.

```
gedit ~/.profile
```
Add lines that say:

```
PATH=$PATH:$HOME/bin
export PATH
```
Logout and log back in to make the change active.

Type 
```

echo $PATH
```
This will show you all the directories that are searched when you type a command. 

Put app in bin.

After doing this, you will be able to type 
"app" and the terminal will search ~/bin for any executable named app and run it if it finds it.

---

### Post by dje on 2008-10-12
try this:
```
sudo cp /path/to/app /usr/local/bin
app
```

hope that helps
dje

---

### Post by aysiu on 2008-10-12
This may work: ```
sudo mv */path/to/app* /usr/local/bin/
sudo chmod +x /usr/local/bin/app
```

---

### Post by bab1 on 2008-10-12
Post #2 is how it normally is done.  If you add ~/bin (your home/bin) to your PATH then only you can run the app.  If you do it as Post#3 the any logged in user can execute it.

The devil is in the details.

---

### Post by Christofferh on 2010-08-26
> **unutbu said:**
> Make a directory to put your executables. Let's say, ~/bin.

```
gedit ~/.profile
```
Add lines that say:

```
PATH=$PATH:$HOME/bin
export PATH
```
Logout and log back in to make the change active.

Type 
```

echo $PATH
```
This will show you all the directories that are searched when you type a command. 

Put app in bin.

After doing this, you will be able to type 
"app" and the terminal will search ~/bin for any executable named app and run it if it finds it.

I found this thread through a google search today and for others that may do so aswell I can say that at least since ubuntu 10.04.1 the /home/<username>/bin directory is added by default at login if the directory exists.

I had trouble to get it to work after creating the /home/<username>/bin directory cause I thought a restart of my terminal software(I'm using Yakuake) would be enough but apparently not.

So in short:
[LIST=1]
[*]Create the directory "/home/<username>/bin" if it doesn't exist
[*]Logout
[*]Login again
[*]Open a terminal and run "echo $PATH"
[*]/home/<username>/bin should be listed in the PATH
[/LIST]

---

