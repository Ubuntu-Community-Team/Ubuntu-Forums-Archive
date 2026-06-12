---
title: "Creating Buttons..."
date: 2008-08-05
forum: General Help
---

### Post by iamBevan on 2008-08-05
Is there a way I can create a button that opens Terminal that automatically runs a particular command?

---

### Post by Ingenue on 2008-08-05
I know how to make a button that opens a Terminal, but not one that opens for a specific command. I'd like to know though.

---

### Post by tamoneya on 2008-08-05
right click on the desktop and select "create launcher".  For type select: "application in terminal" give it a name and then put the command you wish to run in the "command" field.

---

### Post by iamBevan on 2008-08-05
It works... However, the window closes straight away :(

---

### Post by fragos on 2008-08-06
You might try putting the command in a shell script and adding a "read" command which requests input and holds the window open. "Enter" will satisfy read and the terminal window should close.

---

