---
title: "help:problem when installing compiz"
date: 2008-12-01
forum: General Help
---

### Post by skyworld on 2008-12-01
Hi,

when i am installing compiz as command: compiz --replace, I got such feedback from prompt: 

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present. 
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.

I checked my directory and there is no path as /apps/.... Can anybody help me to finish this installation? thanks very much.

---

### Post by binbash on 2008-12-01
you can browse that path via gconf-editor.I saw this problem a couple of times (exact same error) at the forum and ppl fixed it via re-installing compiz

or you can browse that path and reset the value.

---

### Post by skyworld on 2008-12-01
Thank you for your reply. I checked the path and there is no path as the prompt mentioned. And I tried to reboot and install compiz again, but the same problem.

can you explain "or you can browse that path and reset the value"? How can I reset the value?

---

### Post by Forlong on 2008-12-01
> **skyworld said:**
> 
```
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.
```
Here's how to fix that:
```
gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled
```

---

### Post by skyworld on 2008-12-02
Hi,
I checked the my system with compiz-check and get such results:

Gathering information about your system...

 Distribution:          Ubuntu 8.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
 Driver in use:         intel
 Rendering method:      Xgl

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [SKIP]
 Checking for non power of two support...          [SKIP]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [ OK 

I don't know why there are two items skipped, but I suppose this should be ok because there is no item failed.

I then run command as you indicated:

gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled

Then I run command: compiz --replace

Here is the result: 

Checking for Xgl: present. 
Checking for nVidia: not present. 
Checking for Xgl: present.

The cursor flashes and there is no response. If I press ctrl-c, then the system halt -- I have to reboot. I think I have followed the instructions but still failed. Do you have further idea? Thank you very much.

---

### Post by Forlong on 2008-12-02
It skips because you have Xgl installed. You don't need Xgl on an intel chip.
Remove it:
```
sudo apt-get remove xserver-xgl
```
Then restart X and try again.

---

### Post by loomsen on 2008-12-02
Wow, another intel prob. Whole day long.


(Grüße nach Köln btw ^^)

---

### Post by skyworld on 2008-12-02
Hi,

I removed xgl and reboot the computer, then I run " gconftool-2 -s -t string /apps/compiz/plugins/scale/allscreens/options/initiate_edge Disabled" and "compiz --replace" and the prompt displays as follows:

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:3582 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
then cursor flashes and long time waiting until I lose patience.

If I press ctrl-c, then I have to reboot the computer to make it to normal state. It is very interesting that even though I can't install compiz through terminal, I do find "advanced desktop effects settings" in my system menu. How does this happen? Can anybody help me? thank you very much.

---

### Post by Forlong on 2008-12-03
Can you post the output of Compiz-Check now, please?

And what exactly happens when running Compiz?
When you say the "cursor flashes and there is no response", do you mean the desktop freezes?


P.S. you don't need to run that gconftool command anymore.

---

