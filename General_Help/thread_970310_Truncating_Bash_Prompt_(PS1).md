---
title: "Truncating Bash Prompt (PS1)"
date: 2008-11-04
forum: General Help
---

### Post by xienoph on 2008-11-04
I'm trying to make my bash prompt displays the current directory. But, if the absolute path length is longer than 18 characters long, it takes the first 5 characters and last 10 characters, and replace the rest of the path by "...".

For example:
/home/some/really/long/name/blah/blah

becomes:
/home.../blah/blah $


This is what I have:
```

PS1='\[$( 
        TXT=$(pwd -P);
        PRE_LEN=5;
        POST_LEN=10;
        if [ $(( PRE_LEN + POST_LEN + 3 )) -lt ${#TXT} ]; then 
            TXT=${TXT:0:$PRE_LEN}'...'${TXT:$(( ${#TXT} - POST_LEN )):$POST_LEN}
        fi
        echo $TXT;
    )\]:$ '

```

Problem is, as soon as I type something, when I press "Home" or "Ctrl-A" (to go to the start of the line) the cursor always moves to position 3. It seems that Bash cannot remember the length of the prompt.

Anyone know what I did wrong?

---

### Post by cdtech on 2008-11-04
Here are a couple of links to some valuable information on Bash Prompts and the available color codes:
[http://www.ibm.com/developerworks/linux/library/l-tip-prompt](http://www.ibm.com/developerworks/linux/library/l-tip-prompt)
[http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/index.html](http://www.tldp.org/HOWTO/Bash-Prompt-HOWTO/index.html)

And a couple of aliases that I use you can probably compare with.

Hope this helps ya......

**Update::.**
forgot to add the aliases -
```
alias ps1_orig="PS1='${debian_chroot:+($debian_chroot)}\u@\h:\w\$ '"
alias ps1_short="PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\W\[\033[00m\]\$ '"
alias ps1_long="PS1='${debian_chroot:+($debian_chroot)}\[\033[01;32m\]\u@\h\[\033[00m\]:\[\033[01;34m\]\w\[\033[00m\]\$ '"
```

---

### Post by xienoph on 2008-11-04
Thanks for the reply! Turns out that bash ignores the non printing section when calculating for the "length" of the prompt. I got around this by moving the prompt to a new line. Here's my code:

```

PS1='\n\[$( 
        TXT=$(pwd -P);
        PRE_LEN=10;
        POST_LEN=10;
        if [ $(( PRE_LEN + POST_LEN + 3 )) -lt ${#TXT} ]; then 
            TXT=${TXT:0:$PRE_LEN}'...'${TXT:$(( ${#TXT} - POST_LEN )):$POST_LEN}
        fi
        echo $TXT;
    )\]\n[\t]\$ '

```

Still, I prefer to have the prompt on the same line as the directory path. Any idea on how to do this?

---

