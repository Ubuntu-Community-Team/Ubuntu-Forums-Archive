---
title: "ssh tunneling through multiple servers"
date: 2008-11-14
forum: General Help
---

### Post by anlag on 2008-11-14
So my situation is that I need to fetch data from a certain server, which I can only reach by connection to it via two other servers. I start from my local machine, connect to A, from there connect to B, and from there connect to C. The data is on C.

To make things more interesting, I've got one username locally, another one on A and B (userAB) and a third one on C (userC.) I don't have sudo or root access at any of the involved machines.

Seems to me I should be able to just make a nestled ssh tunnel, stepwise... so I've done the following:

On my local machine:

> ssh -f -N -L6969:localhost:6969 userAB@A

On A:

> ssh -f -N -L6969:localhost:6969 userAB@B

And on B:

> ssh -f -N -L6969:localhost:22 userC@C


Now, having done this if I on A execute the following:

> scp -P 6969 userC@localhost:/some/path .

and it works fine! The specified file is fetched from machine C, directly to A through the tunnel. However when I execute exactly the same on my local machine, it asks me for the password of userC@localhost which I do not have, and should not need due to the setup.

The only thing I can think of is that when I connect from my local, C sees my local username and doesn't permit the password-free logon. Whereas when I connect from A, it sees me as userAB which is the same as it would when I connect from B in the 'normal' setup.

Grateful for any suggestions, in how to fix this or a workaround. Cheers.

---

### Post by beercz on 2008-11-14
I don't know if [this]("http://www.unixwiz.net/techtips/ssh-agent-forwarding.html") will help, but I think you need to look at ssh agent forwarding.

---

