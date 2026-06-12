---
title: "Running scripts sh or ./?"
date: 2008-08-19
forum: General Help
---

### Post by wizardfait on 2008-08-19
I've followed a few tutorials and read a few pages and they've always in the end told me to run a script by either sh <script name> or ./<script name>.

I understand that ./ just means current directory/item, but what's the real difference between these two commands?

---

### Post by p_quarles on 2008-08-19
> **wizardfait said:**
> I've followed a few tutorials and read a few pages and they've always in the end told me to run a script by either sh <script name> or ./<script name>.

I understand that ./ just means current directory/item, but what's the real difference between these two commands?
The first one runs the script with the OS's default shell (Dash in Ubuntu, Bash in most Linuxes). The second runs it in the shell defined in the script, which can be anything from Bash/Dash to Perl, Python, PHP, C or Java.

---

### Post by cdtech on 2008-08-19
> I understand that ./ just means current directory/item, but what's the real difference between these two commands?

You have to give bash the path to the script if it is not within your $PATH environment or tell bash its a script with the "sh". You can also use "bash thescript.sh" to do the same thing. This is true with all scripts run from the command line. To get around having to type the "./ - bash - or sh" you could create a directory "~/scripts" to store all of your scripts and add the directory to the PATH variable:
```
export PATH="$PATH:~/scripts"
```
Now you can exicute any script within the "~/scripts" directory from anywhere without the "./ - bash - or the sh".

---

