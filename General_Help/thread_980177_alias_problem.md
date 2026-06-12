---
title: "alias problem"
date: 2008-11-12
forum: General Help
---

### Post by aaronmarsh632 on 2008-11-12
Hi, I created some aliases yesterday which worked fine.

But today I installed a clean copy of ubuntu on my other laptop and did exactly the same but the commands only work for the root user. I created the file ~/.commands to store the aliases in. How can I make all users make use of the aliases I created?

Thanks

Actually I just realized the aliases never worked on other accounts, I was actually logged in as root and forgot. So is there a way I can change this??

---

### Post by Pro-reason on 2008-11-12
Do this:
```

gksu gedit /etc/bash.bashrc

```

And insert this:
```

## Use Aaron's aliases for everyone if the file exists
if [ -f /home/*aaronmarsh*/.commands ]; then
    . /home/*aaronmarsh*/.commands
fi

```
Make sure the path is correct.

Save and close.

---

