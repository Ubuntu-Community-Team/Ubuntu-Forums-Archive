---
title: "New Ubuntu installation fails on user login (Gnome related)"
date: 2008-10-01
forum: General Help
---

### Post by Wayne Vinson on 2008-10-01
I just did an install of Ubuntu 8.04 on an AMD box I don't know too many details about hawdware wise.  This is the first time I've used Ubuntu.  The installation went smoothly - all hardware appears to work etc.  However, I have the following problem:

When the user account created via installation tries to log in with the session choice set to either Gnome or the last session, the login gets just past the point where it makes some jungle noises, the screen goes kind of funny, and then it kicks me back out to the login prompt.  Logging in in failsafe or terminal mode works fine.  If I log in in terminal mode, I can run "gnome-session --failsafe" and it works but running "gnome-session" blows up as above.  I haven't had any luck finding an obvious culprit error message either on the terminal or in .xsession-errors

It seems fairly certain to me that something in the session managment and/or login script is the culprit.  But I've had no luck finding said scripts or figuring out exactly what gnome-session is doing in each case.  Can someone suggest a debugging course of action that will allow me to determine what the culprit is?

---

