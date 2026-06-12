---
title: "hard drive noise while playing movie over network-going insane"
date: 2008-10-02
forum: General Help
---

### Post by BlueFiberOptics on 2008-10-02
I've been trying to solve this problem for a long time.  It's the last thing keeping me from using Ubuntu full time on my HP notebook.

Here is the situation:

I'm using Ubuntu 8.04 with ndiswrapper on my notebook.

When I access a Windows shared folder on the network and play a movie file, my notebook hard drive seeks annoyingly loud.  This DOES NOT OCCUR with Windows XP.  I'm just trying to figure out what is causing the harddrive to be so noisy and what I can do to make it more quiet when I'm watching a movie over the network.


If anyone could ever help me solve this problem, I will be eternally grateful!

---

### Post by DropEffect on 2008-10-02
Have you made sure that Ubuntu isn't downloading the video from your network into temp instead of streaming it?

---

### Post by BlueFiberOptics on 2008-10-02
What exactly do you mean?

Are you talking about when a dialog box comes up and actually shows the file copying first to my hard drive to try and play?&#12288;&#12288;I don't get this dialog box unless there is a problem.

Or are you talking about something that I am not visually supposed to see?

By the way, thanks for taking the time to respond!

---

### Post by russo.mic on 2008-10-02
Are you using Samba?  I'm fairly certain that it is probably copying the file to the HD in the background to play it back, which is probably why that is happening.

---

### Post by BlueFiberOptics on 2008-10-02
Yes, I believe I am using samba.  In the location bar it uses smb:/// etc before I open the file

---

