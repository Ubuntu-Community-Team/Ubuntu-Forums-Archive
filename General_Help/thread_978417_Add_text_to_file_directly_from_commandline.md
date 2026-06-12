---
title: "Add text to file directly from commandline"
date: 2008-11-11
forum: General Help
---

### Post by mashcaster on 2008-11-11
It I have a commandline installation, I know I can do stuff like the following to open up an editor to add text to a text file

sudo nano /etc/apt/sources.list

I can then type in what I want and save as normal.

Is it possible to do this directly from commandline without opening up an editor, i.e. somehow pipe in the new text into the text file?

I am sure I have seen this done before, but can't seem to find the threads which show how to do this.

I think it involved having an > in the commandline?

Something like

text to be entered > /etc/apt/sources.list

Anyone know what I am talking about?

---

### Post by geirha on 2008-11-11
If you are the owner of the file, then you can do something like this:
```

# This will empty (truncate) *filename* and add one line
echo "Line to be added" > *filename*

# This will append a line to the end of *filename*
echo "Line to be added to the end of the file" >> *filename*
# One > overwrites, two >> appends.

```

If you need root priviledges though, doing **sudo echo "something" >> *filename***, will not work because the >> is interpreted by the shell and not by echo.

You can use tee for such purposes
```

echo "Line to be added at the end" | sudo tee -a *filename*

```

Tee will print the line both to the file and to stdout (terminal window). Don't forget the -a option to tee. -a is for appending, without it you overwrite like with >.

---

### Post by mashcaster on 2008-11-11
So if I wanted to add a repository to the sources.list file, I would do something like this?

> echo "deb [http://ppa.launchpad.net/lxde/ubuntu](http://ppa.launchpad.net/lxde/ubuntu) hardy main" | sudo tee -a /etc/apt/sources.list

I am not using Linux at the moment, so I cannot test this out.

Will this then ask for the password before appending the file?

---

### Post by geirha on 2008-11-11
Yes, that should add the repository to your sources.list. And if you haven't run something with sudo in that terminal for the last fifteen minutes, it will ask for your password. sudo remembers your password for about fifteen minutes, so running two sudos right after each other only requires you to type the password once.

BTW, it doesn't have to be in sources.list. In addition to reading /etc/apt/sources.list, it reads /etc/apt/sources.list.d/*.list, so I ususally put third-party repositories in seperate files.  

```
echo "deb http://ppa.launchpad.net/lxde/ubuntu hardy main" | sudo tee /etc/apt/sources.list.d/lxde.list
```

---

### Post by mashcaster on 2008-11-11
> **geirha said:**
> Yes, that should add the repository to your sources.list. And if you haven't run something with sudo in that terminal for the last fifteen minutes, it will ask for your password. sudo remembers your password for about fifteen minutes, so running two sudos right after each other only requires you to type the password once.

BTW, it doesn't have to be in sources.list. In addition to reading /etc/apt/sources.list, it reads /etc/apt/sources.list.d/*.list, so I ususally put third-party repositories in seperate files.  

```
echo "deb http://ppa.launchpad.net/lxde/ubuntu hardy main" | sudo tee /etc/apt/sources.list.d/lxde.list
```

I learnt 2 new things today! :D

---

### Post by mashcaster on 2008-11-11
What if I wanted to add 2 lines to the same file?  Do I have to run that command twice, or is there a simpler way of doing it?

For example, I may want to add something like this to:
/etc/apt/sources.list.d/lxde.list

> deb [http://ppa.launchpad.net/lxde/ubuntu](http://ppa.launchpad.net/lxde/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/lxde/ubuntu](http://ppa.launchpad.net/lxde/ubuntu) hardy main

---

### Post by iponeverything on 2008-11-11
You could also do:

cat >> file.txt

Input your text then type Ctrl-D

Also make sure that all your lines end with a Newline
(i.e. "Enter")

---

### Post by geirha on 2008-11-11
I'd do:
```
sudo tee /etc/apt/sources.list.d/lxde.list << EOF
deb http://ppa.launchpad.net/lxde/ubuntu hardy main
deb-src http://ppa.launchpad.net/lxde/ubuntu hardy main 
EOF

```

---

### Post by iponeverything on 2008-11-11
This is why I love unix. Streams, pipes, IO redirection, and process management -- just to name a few. It's an OS designed by and for linear thinking geeks like me.  There is no right or wrong way to do most things, it's like lego's for the mind.

---

### Post by mashcaster on 2008-11-11
Although the EOF is a nice feature, is it possible to do a similar thing without having to use the <enter> key?

---

### Post by geirha on 2008-11-11
Not sure what you mean ... you can have echo output multiple lines too. 
```
echo -e "deb http://ppa.launchpad.net/lxde/ubuntu hardy main\ndeb-src http://ppa.launchpad.net/lxde/ubuntu hardy main" | sudo tee...
```

---

### Post by koenn on 2008-11-11
> **mashcaster said:**
> Although the EOF is a nice feature, is it possible to do a similar thing without having to use the <enter> key?

if you run it from a script, you won't have to Enter. If you're not running a script, you have to press Enter after every line you type anyway.

you can also do
```

( echo "something"
echo "something else"
) >> somefile

```

to avoid all the sudo stuff in your commands, and the workarounds associated with it, you can also just
a/ open a root session with 'sudo -i', then do whatever it is you' want to do, then exit
or
b/ put all your stuff in a script and run the entire script with sudo

---

### Post by -Zeus- on 2008-11-11
you don't nessecarily need to use tee, a workaround is
```
sudo sh -c "echo blah >> /etc/fstab"
```

---

