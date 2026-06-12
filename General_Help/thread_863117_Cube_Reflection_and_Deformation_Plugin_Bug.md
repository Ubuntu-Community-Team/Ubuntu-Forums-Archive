---
title: "Cube Reflection and Deformation Plugin Bug"
date: 2008-07-18
forum: General Help
---

### Post by irshadcharm on 2008-07-18
**1) Linux User Level:** Beginner

**2) OS:** Ubuntu 8.04.1 Hardy

**3) Kernel:** 2.6.24-19-generic

**4) Compiz Fusion Version:** 0.7.6

**5) Plugin:** Cube reflection and Deformation

**6) Issue: **

         [LEFT]> Since I've updated my compiz fusion 0.7.4 to 0.7.6 from the repos , all the plugins work efficiently except the plugin that i've mentioned above. Sometimes it's stable and many a times its erratic. **_There are no error messages as of now but the issue is when i try to rotate the cube I'm getting a choppy background of the existing window. When I disable  and enable the plugin things are subtle but again the trouble arises._** Compiz is completely supported with my machine, so there are no issues with my xgl. I'm really stumped. Help would be appreciated to the core.[/LEFT]

**7) Solution:**
[LEFT]>  Please flood in your valuable replies. :confused::confused::confused:[/LEFT]

---

### Post by haegl on 2008-07-18
Can you post a screenshot?

---

### Post by irshadcharm on 2008-07-18
Please give some instructions on how to do that?

---

### Post by haegl on 2008-07-18
Press print-screen while rotating the cube :)

---

### Post by irshadcharm on 2008-07-18
I'll post the screenshot asap...thx for the reply...

---

### Post by haegl on 2008-07-18
sorry, wrong thread...

---

### Post by irshadcharm on 2008-07-18
I've attached the screenshot ....any help wud be appreciated...

---

### Post by damis648 on 2008-07-18
Are you sure you are using 0.7.6? I am up to date and only have 0.7.4. Run
```
compiz --version
```
in terminal and tell us what you see.

---

### Post by irshadcharm on 2008-07-18
**Input:** compiz --version

**Output:**
> Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
compiz 0.7.6

---

### Post by damis648 on 2008-07-18
> **irshadcharm said:**
> **Input:** compiz --version

**Output:**

I just added extra repos from the launchpad PPA. It was in those repos. Sorry, I thought you meant the default repos. I just updated and will reboot and let you know if I have similar issues.

---

### Post by irshadcharm on 2008-07-18
By adding the repos to third party sources, compiz updates itself to the recent version i suppose.

```
deb http://ppa.launchpad.net/compiz/ubuntu hardy main
```

```
deb-src http://ppa.launchpad.net/compiz/ubuntu hardy main
```

---

### Post by irshadcharm on 2008-07-18
> **damis648 said:**
> I just added extra repos from the launchpad PPA. It was in those repos. Sorry, I thought you meant the default repos. I just updated and will reboot and let you know if I have similar issues.

Ok bro waiting for your valuable reply....Each and every time i need to reload my window manager using compiz icon to get rid off the bug.

---

### Post by damis648 on 2008-07-18
> **irshadcharm said:**
> Ok bro waiting for your valuable reply....Each and every time i need to reload my window manager using compiz icon to get rid off the bug.

Sorry, I've got none of these issues.

---

### Post by irshadcharm on 2008-07-18
Is there anyone to help in this issue? This is really driving me crazy....

---

### Post by irshadcharm on 2008-07-18
more than 100 views but no replies...whats wrong?

---

### Post by irshadcharm on 2008-07-19
Humbly waiting for replies for my issue...

---

### Post by DaymItzJack on 2008-07-19
Compiz and it's plugins will work for a lot of people, but it's not guarantied to work on all systems for all video cards.

You can try to reinstall compiz or just accept that it might not work for you, or continue to slowly beg for answers when there probably will be none.

---

### Post by irshadcharm on 2008-07-19
> **DaymItzJack said:**
> Compiz and it's plugins will work for a lot of people, but it's not guarantied to work on all systems for all video cards.

You can try to reinstall compiz or just accept that it might not work for you, or continue to slowly beg for answers when there probably will be none.

If u can't help just move on...Since other plugins work efficiently there will be a way to solve this issue as well...i dont wanna beg for answers as there are many users who will reply...

---

### Post by DaymItzJack on 2008-07-19
Those "other plugins" that work fine aren't as complex as the cube deformation one.

---

### Post by irshadcharm on 2008-07-25
Do anyone have an answer for my issue?

---

### Post by yuki86 on 2009-03-09
hey man im with you i got same problem, i got two different video cards, trying git compiz witch no change, i gues in git is 0.7.8 same as in ubuntu repos, maybe not i dont know, but yes it sucs, i want transparent caps, if anybody know how to do it without enabling that ref. and derform. pls let me know

[[IMG]http://img401.imageshack.us/img401/6264/snmekobrazovky.th.png[/IMG]](http://img401.imageshack.us/my.php?image=snmekobrazovky.png)

edit: i install newest compiz 0.8.3from git and same error again

---

### Post by naarkhoo on 2009-11-18
I have same problem,

 My cylinder deformation JUST stopped working, I used Fusion-icon to change settings, reload, switch managers, and in settings I enabled sphere/cube and turned them on and off, it just seems **the plugin** has died. becuase other feature works perfectly,

Using 'compiz-check' gets a list of green OK's and it seems okay apart from the deformation.

Any ideas?

---

