---
title: "Annoying login problem"
date: 2008-07-23
forum: General Help
---

### Post by minhdinh on 2008-07-23
i dont know what happened but now everytime i log into ubuntu i get this message and i dont know what to do to fix it!!!!BTW im a linux noob so it would help to have step by step instructions on how to fix this problem. the message is 

"User's $HOME file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's Home directory must be owned by user and not writable by other users."


PLEASE HELP ME FIX THIS PROBLEM!!!

---

### Post by iaculallad on 2008-07-23
Drop to your terminal and do the following commands below one-at-a-time:

```
sudo chmod 644 /home/your_user_name/.dmrc
sudo chown your_user_name /home/your_user_name/.dmrc
sudo chmod -R 700 /home/your_user_name
sudo chown -R your_user_name /home/your_user_name
```

And restart:

```
sudo shutdown -r now
```

---

### Post by minhdinh on 2008-07-23
Wow it worked and thanks for the crazy fast reply!!!

---

### Post by iaculallad on 2008-07-23
> **minhdinh said:**
> Wow it worked and thanks for the crazy fast reply!!!

No problem, Glad to be of help. Go Ubuntu.

---

