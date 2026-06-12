---
title: "Bash script looking for symbolic link"
date: 2008-11-13
forum: General Help
---

### Post by chiefchief on 2008-11-13
Hey guys.  My collegue and I wrote a bash script that is supposed to see if the user has a symbolic link already on their desktop, and if they don't, create one.  Here's an example:
```
if [ ! -L "~/Common" ];
then
    ln -s /company/Common ~/Desktop
fi

```
Unfortunately, it runs the ln command whether the Common link is ther or not, which makes me think that my statement ```
if [ ! -L "~/Common"];
``` must be wrong.

Any advice would be greatly appreciated, I am by no means a scripting genius.

Thanks!

---

### Post by Portmanteaufu on 2008-11-13
Maybe I've misread this, but it seems like you're checking if there's a link to "Common" in their home directory: 

```
if [ ! -L "~/Common" ];
```

rather than if there's a link to Common in their ~/Desktop folder. I'm away from a shell at the moment so I can't test this, but I think you're looking for: 

```
if [ ! -L "~/Desktop/Common" ];
```

---

### Post by chiefchief on 2008-11-13
Thanks for the quick reply.  That was definetly a typo.  I corrected it, still having the same issue.  I also tried using this, which didn't work either:
```
if [ ! -L "/home/**${USERNAME}**/Desktop/Common" ];
then
   echo ln -s /woodfeathers/Common ~/Desktop
fi

```

---

### Post by Portmanteaufu on 2008-11-13
This is probably another typo, but you've got 
```
echo ln -s /woodfeathers/Common ~/Desktop
```

Where you're "echo"ing instead of "ln"ing. Could you copy / paste from the original code?

---

### Post by chiefchief on 2008-11-13
Sorry for the confusion.  I edited some pieces to show you what I was doing.  I'm having it echo right now instead of actually linking.  This is the code as it is right now:
```

if [ ! -L "~/Desktop/Common" ];
then
   echo ln -s /woodfeathers/Common ~/Desktop
fi
```

Now I have a link to Common on my desktop.  If I run the script, it should not echo anything, but it echos "ln -s /woodfeathers/Common ~/Desktop"

---

### Post by Portmanteaufu on 2008-11-13
Strange. That seems pretty valid to me. Would you mind posting the output of 
```
ls -all ~/Desktop | grep Common
```
?

---

### Post by chiefchief on 2008-11-13
```
lrwxrwxrwx  1 administrator administrator     21 2008-11-13 11:19 Common -> /woodfeathers/Common/

```

---

### Post by Portmanteaufu on 2008-11-13
Wild. It turns out the if statement fails (on my box) because I put the link name in quotes. Try it again like this: 

if [ ! -L ~/Desktop/Common ];
then
   echo ln -s /woodfeathers/Common ~/Desktop
fi

and let me know if it works. Does anybody know why the quotes cause weirdness?

---

### Post by Portmanteaufu on 2008-11-13
Oh, duh. Nevermind, I answered my own question. Because we're using double-quotes, the tilde we're using to represent the home directory isn't interpreted. It's literally looking for a file with a "~" character in the path. Obviously, that doesn't exist, so it fails to find it.

---

### Post by Portmanteaufu on 2008-11-13
Also (how prolific am I?), in the alternate test scheme you tried above: 
```
if [ ! -L "/home/${USERNAME}/Desktop/Common" ];
```
there isn't normally a $USERNAME variable. There is, however, a $USER variable. Using the modified 
```
if [ ! -L "/home/${USER}/Desktop/Common" ];
```
worked on my machine too.

---

### Post by chiefchief on 2008-11-13
Thanks so much for the help!  I'm about to test it out, I'll let you know if it worked.

---

