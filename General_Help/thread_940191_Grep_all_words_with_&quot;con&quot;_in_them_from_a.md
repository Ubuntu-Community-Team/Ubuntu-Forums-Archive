---
title: "Grep all words with &quot;con&quot; in them from a dictionary?"
date: 2008-10-06
forum: General Help
---

### Post by wubrgamer on 2008-10-06
Is it possible to grep all words with the string "con" "Con" "CON" etc. etc. from a dictionary?

for instance "magic command 'con' dictionary" will spit out words such as Confluence, contended, inconceivable etc etc.

I really need this! Thank you!

---

### Post by ghostdog74 on 2008-10-06
```

grep -i "con" file

```

---

### Post by taladan on 2008-10-06
+1 ghostdog74 - though you don't necessarily have to have the "'s around con, it won't hurt to get in the habit of using them.

Tal

---

### Post by wubrgamer on 2008-10-06
where is the file?

/usr/share/dict/words is just a pointer to a non-existant file on my machine

does this command work on yours?

could you test it? or at least tell me where the dictionary file is on my ubuntu installation? (it's actually an xubuntu installation, i might need to install the ubuntu core packages...but yeah, if you could tell me where the real file is I'd really appreciate it!)

---

### Post by ghostdog74 on 2008-10-06
i do have that file.
for your case, not sure, but you can always search for it
```

find / -type f -name "words"

```

---

### Post by wubrgamer on 2008-10-07
So, I just ran the command "grep -i con /usr/share/dict/words" on both an ubuntu (regular gnome)machine and a dreamhost debian 2.4.x kernel series installation

they both gave me the word lists I was looking for

**_*BUT*_** I cannot do this on my **_*x*_**ubuntu machine....

also, I believe that pidgin's spellcheck isn't working correctly

what packages do i need to install on my xubuntu installation that are concerning this, that are on my ubuntu installation, but not my xubuntu installation...?

---

### Post by wubrgamer on 2008-10-07
I believe this is a fault with the xubuntu core installation that might need to be fixed...as it should already be there...

could someone additionally explain what the difference is between the dictionary files in xubuntu and ubuntu? or is it a difference in the spellchecking?

thank you!

---

