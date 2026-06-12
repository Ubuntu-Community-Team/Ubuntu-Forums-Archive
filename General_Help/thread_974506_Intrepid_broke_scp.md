---
title: "Intrepid broke scp"
date: 2008-11-07
forum: General Help
---

### Post by valadil on 2008-11-07
I updated my desktop to Intrepid a week ago.  Today I noticed that scp isn't working between my work and home computer.

me@work:~$ scp home:file .
protocol error: unexpected <newline>

me@home:~$ scp file work:
(and it just pauses here for a while after I authenticate)

Now, the interesting thing is that if I log in at home, I can scp to my dreamhost account.  That works fine.  But I can't log in at dh and scp from home.  I haven't seen any errors scping between work and dh so far.

My firewall is disabled.  I haven't made any changes to my router lately.  ssh works great, it's just scp that's problematic.  

I was suspicious of sshd_config because upgrading to Intrepid overwrite a number of my files in etc, but my settings in sshd_config look intact (namely disabling password based login).  I'd post the file, but no scp.  

Any ideas?

---

