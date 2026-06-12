---
title: "File searches using Linux"
date: 2008-10-11
forum: General Help
---

### Post by darkan9el on 2008-10-11
Hi all, I have seen in a few help tutorials where file searches are performed and the $ symbol is placed before a folder or file name; what does the $ symbolise/mean.

The reason I am asking is, I have a friend who has a problem on Vista x86 and it relates to a hard to find file called txflog or as the tutorial shows $txflog, this file needs to be removed because it is preventing him from repairing Vista - Microsoft do love there software loops Hmmm! the txflog file is actually a dll file and relates to the Common Log File System driver (clfs.sys)

As an example here is the code used:

```
cd /mnt/windows/\$Extend/RmMetadata
rm -rf \$TxfLog
```

The original text is> 4. Navigate to the hidden folder: "cd /mnt/windows/\$Extend/RmMetadata". Note the backslash before the $; that is important as it keeps the command shell from interpreting the $ (it is really part of the file name).
5. Take a deep breath and recursively remove the $TxfLog file: "rm -rf \$TxfLog". Use "ls" to verify that it has been deleted.
6. "cd /", "umount /mnt/windows", and "init 6" to reboot, removing the CD when appropriate.

I am curious and what to understand the 'why it's there' reason.

The original help tutorial is: [Here]("http://bsods.com/content/windows-vista-and-stop-0x0000c1f5-linux-anyone")

regards Lee

---

### Post by geirha on 2008-10-11
> **darkan9el said:**
> Hi all, I have seen in a few help tutorials where file searches are performed and the $ symbol is placed before a folder or file name; what does the $ symbolise/mean.


The $ is a special character in unix shells, meaning that the next part is a variable name. (Windows uses %varname% while linux uses $varname)

```
read -p "What is your name? " name   # Reads user input into the variable called name (not using $ when assigning the variable)
echo "Hello, $name, nice to meet you"  # When reading the name variable, the $ is used.

```

That's why you need to put a \ infront of $ in linux, to avoid it being treated as a variable. It's called escaping special character.

In windows, files/folders starting with $ probably has a special meaning, but in linux, you generally try to avoid using that character in files/folders.

---

### Post by darkan9el on 2008-10-11
thank you very much for the explanation, this helps me alot to understand the syntax for the code, makes it much clearer.

regards Lee

---

