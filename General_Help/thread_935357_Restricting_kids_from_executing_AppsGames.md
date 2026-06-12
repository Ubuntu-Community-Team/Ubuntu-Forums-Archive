---
title: "Restricting kids from executing Apps/Games"
date: 2008-10-01
forum: General Help
---

### Post by bkaplan on 2008-10-01
I'm trying to figure out if there is a way to keep certain users (e.g., my kids) from executing a category of installed applications (e.g., Games) from their own profile/login accounts.

I'd really love to be able to make the execution of installed games a permission based action (e.g., admin authentication -based, or the like), so that I can keep them focused on schoolwork until they get parental permission to play.

I'm a relatively experienced computer user, but have < 1 year experience with Ubuntu, so thanks for as many details as you can provide (assuming there is a solution).

Thanks!

---

### Post by nsche on 2008-10-02
Create a games group and make all of the games belong to that group.  Change the permissions on all of the games to 550.  Add the games group only to the accounts of those you want to be able to run the games.

Have fun
Norm

---

### Post by russo.mic on 2008-10-02
Or, better yet, to decide when they can play, you could change the permissions of the games "executables" to root, then put gksudo in front of the shortcuts.  then you'd be asked a password to play the game.

Russo

---

### Post by Peter09 on 2008-10-02
You could make another user - say gameplayer - who owns all the games and execution rights. Then to play a game your kids would have to login through that account.

---

