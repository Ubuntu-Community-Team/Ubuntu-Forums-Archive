---
title: "New install server 8.10 can't type password"
date: 2008-12-18
forum: Installation &amp; Upgrades
---

### Post by Walway on 2008-12-18
I know 0 about servers but would like to learn.  I took an old
P4 with xppro installed and loaded server from mailed CD.  It all installed and alowed me to boot to server. When the user name and password screen came up I could put in the user name but It does not allow me type anything in the password screen. I have installed it 3 times on this computer 3 times with different usernames and passwords with the same results.  Is there some trick to this.  One example- I made the user name salem and the password salem which is what I typed exactly in the user name box but I could not type in the password box.

---

### Post by taurus on 2008-12-18
Do you mean you cannot type in the password or when you type in the password, nothing shows on the screen?  In other words, you don't see ***  (dot-dot-dot) on the terminal when you type your password.

---

### Post by Walway on 2008-12-18
I get no *** When I attempt to type the password and the curser does not move

---

### Post by taurus on 2008-12-18
Just keep typing the password and hit Return when you are done.  Now, do you log in?

---

### Post by Walway on 2008-12-18
no- it acts like I have not typed the password.  it times out in 60 seconds and gives me the login screen again.  Same result type username, enter, password screen with blinking curser but will not let me enter anything.  If I hit enter says not correct login

---

### Post by taurus on 2008-12-18
You did type in the correct password even thought the cursor didn't move and nothing showed on the screen when you typed it?

---

### Post by cariboo on 2008-12-18
Just a point, if you are getting a graphical login, you don't have the server installation, as there is no gui installed. If you get something like this:

```
jim@jack:~$
```

You are logged in. If you need a gui, at the prompt type:

```
sudo apt-get install ubuntu-desktop
```

Jim

---

### Post by decoherence on 2008-12-18
The standard behavior for a command line login is to show absolutely nothing when you type your password. Just type it and press enter. If that doesn't work, you either typed it wrong or you customized PAM during the installation, which would be a conscious effort on your part.

Most likely a typo when typing the password.

I suppose it could also be that it doesn't like your username and password being the same... I haven't heard of that before but I have also never made my password match my username.

---

### Post by Walway on 2008-12-18
Being this is my first experience with umbuntu I could have done a number of things.  First I get the scrolling screen with all the loading information then I get a server longin line that Iput the username.  Then password _ appears where the underline is blinking.  My typing  does not register at this point except the enter key.  Then I get a login failed message and prompts me to loging again.  I did finally get a multiple log in failed message with a lot of goblety gook about getting help from the ubutu website and login options andtypes.  It is definitely not a gui.  I have to go for now- holiday program at the school. We are a little charter school.

---

