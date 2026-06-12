---
title: "Anyone here use Git for version control? Help!"
date: 2008-07-22
forum: General Help
---

### Post by noobydev on 2008-07-22
I'm new to Linux and up until the last couple of weeks I didn't even know the simplest of terminal commands (ls, cd, etc!). I'm getting on ok now though and I'm mostly working with remote servers over SSH and SFTP.

I really need to setup Git for a project I'm working on but need some help not just with the actual commands but with strategy.

[LIST]
[*]The original project code lives on the internet somewhere (let's call it Server1)
[*]It gets updated frequently (almost every day)
[*]I need to be able to change the code on my laptop, add extra features etc, while still being able to get the updates from Server1
[*]I need to deploy the code to a production server (Server2) that is basically a mirror of what I have on my development machine (the laptop)
[/LIST]

So far I've just been cloning the git from Server1 to my laptop, working on it there, and then manually uploading to Server2 over SFTP. This way is not great because it's been hard for me to keep up with the frequent updates that are made to the code on Server1. I've pretty much started over 2 or 3 times because the updates were so important!

Can anyone help me get a good system going for this using Git?

---

### Post by noobydev on 2008-07-22
Sorry, I think I should have posted in the programming section, can this thread be moved?

---

