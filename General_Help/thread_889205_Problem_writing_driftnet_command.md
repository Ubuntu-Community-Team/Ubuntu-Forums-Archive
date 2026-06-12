---
title: "Problem writing driftnet command"
date: 2008-08-13
forum: General Help
---

### Post by grEnAlEins on 2008-08-13
I am having a problem writing a command for driftnet and wanted some assistance.  What I want to happen is to have images saved a specific location when I click on them in the driftnet window.

Currently my command reads as follows:
```
driftnet -i eth1 -v -d ~/driftnet/images
```

This places the temp images in the /driftnet/images directory.  When I try to save images via driftnet, they are saved at ~/driftnet/scripts.  I think this is because I store commands as files and run the files as commands in terminal.  I change directories to ~/driftnet/scripts and then run my commands as root using the sh command.  In the case that this does not make sense, I do this:

```
cd driftnet/scripts
```

and then I do this:

```
sudo sh drift-wireless
```

which in turn executes this:

```
driftnet -i eth1 -v -d ~/driftnet/images
```

in terminal.

I want the saved images to be stored in driftnet/images but they end up in driftnet/scripts.  Is this because this is where I run run the command from?  Is there a way to change the location to which files are saved.

I apologize in advance if I was overly redundant.  I just wanted to make sure that I was clear.


Thanks,

Nick:biggrin:

---

### Post by tgalati4 on 2008-10-24
You would have to look at the source code.  It may be a bug.

Rather than fight it, be more creative:

>sudo ln -s /home/you/myimages /driftnet/scripts

This creates a link to where you want your files from a directory that you know gets consistently dumped to.

---

