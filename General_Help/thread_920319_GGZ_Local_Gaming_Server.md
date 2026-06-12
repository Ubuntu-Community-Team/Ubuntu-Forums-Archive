---
title: "GGZ Local Gaming Server"
date: 2008-09-15
forum: General Help
---

### Post by Lord C on 2008-09-15
It seems that all the Gnome Games installed in Ubuntu by default, require you to connect to a central server, for 'Network Play'.

However at college a lot of ports are blocked, so this isn't possible.
What I want to do is setup a local games server. That anyone in college can connect to.

I've found very little documentation of GGZD (ggzgamingzone.org).

I have configured the .conf file, using the .example. And I've created an empty log file, so the server actually runs.

Two other Ubuntu desktops can connect to it, and chat in the game lobby.

However you cannot launch any games.

In the config file there's an option for settings games, which when left blank is supposed to find all games. But if I try specify 'chess' for e.g. I get the following problem;

```
~$ sudo ggzd
(<errorsys>) Unable to read file /etc/ggzd/games//chess.dsc: No such file or directory
(<errormsg>) Ignoring chess, could not open /etc/ggzd/games//chess.dsc
(<errorsys>) Unable to read file /etc/ggzd/rooms//ggzd_casual.room: No such file or directory
(<errormsg>) Ignoring ggzd_casual, could not open /etc/ggzd/rooms//ggzd_casual.room

```

So it looks like there should possibly be a ggzd package to install the games and/or connect different games. But I have no idea.

If anyone could shed some light on this situation that would be great.

---

