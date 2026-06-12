---
title: "Bash help"
date: 2008-11-17
forum: General Help
---

### Post by leg on 2008-11-17
Having a problem with a script I am trying to write. I am trying to write a file from within a script, I am trying this:

```

cat > $FILENAME << "EOF"
export DATA=${varname}
EOF

```

I have tried all the expansion methods I have read from the tldp guides but I think anything between the "EOF" & EOF is written as is. How do I go about creating this file with the variables expanded correctly. 

Thanks

---

### Post by cmnorton on 2008-11-17
Don't quote EOF, and you should get what you want, provided $FILENAME and $varname are not empty.

---

### Post by Keith Hedger on 2008-11-17
No quoting EOF will inhibit paramater substitution, what u need is```
(
cat << EOF
export DATA=${varname}
EOF
) > $FILENAME
```

---

### Post by leg on 2008-11-17
> **cmnorton said:**
> Don't quote EOF, and you should get what you want, provided $FILENAME and $varname are not empty.

Thankyou

---

### Post by leg on 2008-11-18
I also had to remove the space from between the chevron and EOF on the first line. With the space in place my guess is that the space was included as the marker so never matched the EOF I had at the end of the block. So I ended up with:
```

cat > $FILENAME <<EOF
export DATA=${varname}
EOF

```

What resources would you suggest for me to learn more about bash scripting. I have been through the two guides on [tdlp.org]("http://tldp.org/"). Personally I find the test stuff rather confusing at the moment.

---

### Post by Keith Hedger on 2008-11-18
Advanced Bash Scripting Guide (its in the repos look for abs)

---

