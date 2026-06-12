---
title: "i need someones help"
date: 2009-06-15
forum: Installation &amp; Upgrades
---

### Post by blondielegs on 2009-06-15
i am trying to install google earth on to my computer. and its a bin file. how do i do it cause it keeps saying i have nothing to support bin files.

---

### Post by iponeverything on 2009-06-15
right click on it and go to "open with other application" then go to "use custom command" and put "sh" in the box.

---

### Post by Wiebelhaus on 2009-06-15
Use [Ubuntu-Tweak]("http://ubuntu-tweak.com/") It'll the Google repositories and make it all simple.

But to answer your question:


1. Make sure the file is set to "executable" by running this command:
Code:

```
chmod u+x NameOfYourFile.bin
```

2. Run the file like this:
Code:
```

./NameOfYourFile.bin
```

NOTE: If the installer requires access to directories outside of your /home/ directory, you may need to log in as root before you can execute these commands successfully. That can be accomplished with the su command, followed by your root (Administrator) password. Ubuntu users will use sudo and their regular user password instead.

---

### Post by gregh on 2009-06-15
oops, already answered above

The extension bin is short for binary.

To run this file you need to make it executable.

To do this, open the file manager and browser to the file. Right click on it and under the "permissions tab" tick the check box that says "Execute"

Exit the file manager and double click the file.

If you are ok in a command shell this is the command:

chmod u+x filename

where filename is the google earth install file.

-Greg

---

### Post by Wiebelhaus on 2009-06-15
It's funny how many different ways you can things with the Unix base.

---

