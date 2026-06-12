---
title: "grep -b command"
date: 2008-07-11
forum: General Help
---

### Post by rpm048 on 2008-07-11
Hi All.. i was trying this command. It says illegal option maybe its being restricted by our administrator. is there a alternative command to display the context - i.e. 5 lines of context before a match. im using Solaris OS.

[COLOR="Blue"]more test.log | grep -B 5 'This pattern file'[/COLOR]
grep: illegal option -- B
Usage: grep -hblcnsviw pattern file . . .


i just want to search the string "this pattern file" and the above line with "time" [00:00:06]



test.log
[COLOR="Blue"][2008-07-11 00:00:06] ***********************1018
[2008-07-11 00:00:06]  
                        packet data (length:209)
                        2 48 51 58 48 56 51 9 48 50 49 58 48 57 50 57 55
                        55 52 48 52 57 48 9 48 51 51 58 49 47 50 32 84
                        104 101 32 67 97 108 108 101 114 32 82 105 110 103 116 117
                        110 101 44 32 75 65 72 73 84 32 78 65 32 98 121 32
                        83 65 82 65 72 32 71 69 82 79 78 73 77 79 32 104
                        97 115 32 98 101 101 110 32 97 100 100 101 100 32 116 111 This pattern file, blah blah blah
                        32 121 111 117 114 32 74 117 107 101 98 111 120 46 32 89
                        111 117 32 104 97 118 101 32 98 101 101 110 32 99 104 97
                        114 103 101 100 32 51 48 46 48 48 32 118 97 108 105 100
                        32 102 111 114 32 51 48 32 100 97 121 115 46 32 84 111
                        32 115 116 111 112 32 116 104 105 115 32 115 101 114 118 105
                        99 101 32 97 110 9 48 50 51 58 50 55 50 56 9 48
                        54 52 58 50 57 9 48 54 53 58 53 52 9 54 66 3

[/COLOR]
Thanks

---

### Post by ghostdog74 on 2008-07-11
then you don't have GNU grep
```
 # grep --version
grep (GNU grep) 2.5.1

```

---

### Post by dcstar on 2008-07-11
> **ghostdog74 said:**
> then you don't have GNU grep
```
 # grep --version
grep (GNU grep) 2.5.1

```

Funny how a forum that is for "All your general support questions for Ubuntu, Kubuntu, Edubuntu and Xubuntu." gets a question for an unrelated Unix release, isn't it?

---

