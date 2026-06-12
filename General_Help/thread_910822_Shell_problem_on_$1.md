---
title: "Shell problem on $1"
date: 2008-09-04
forum: General Help
---

### Post by registerme on 2008-09-04
I have s1.sh as follows:

#!/bin/sh
. ./s2.sh somearg

and I have s2.sh as follows:

#!/bin/sh
echo $1

when I run ./s1.sh, it is supposed to show 'somearg' as it is passed as $1 s2.sh, but it didn't show up. If I run ./s1.sh xxxx, it shows xxxx, which means $1 is s1.sh's $1.

It runs as expected on Redhat Enterprise 4, is this a bug in ubuntu 8.0.4?

---

### Post by unutbu on 2008-09-04
I don't know much about dash or bash, so I can't explain why this is so, but if you change

#!/bin/sh to #!/bin/bash

you will get the output you are expecting.

On Ubuntu, unlike RedHat, /bin/sh is a symlink to /bin/dash.

---

### Post by aloshbennett on 2008-09-05
tried on my machine and works fine. Can you post the scripts?

---

### Post by registerme on 2008-09-05
> **aloshbennett said:**
> tried on my machine and works fine. Can you post the scripts?

The scripts were posted in my first post, exactly the same. Is your sh linked to dash? I am wondering how comes mine didn't work but yours worked.

---

### Post by Vivaldi Gloria on 2008-09-05
It works for me when the following are in the same folder:

```
#!/bin/bash
./s2.sh somearg
```

```
#!/bin/bash
echo $1
```

The first is named s1.sh and the second one is s2.sh.

```
vivaldi@narval:~/test$ ./s1.sh
somearg
```

In your s1.sh above you've a dot-space-dot. Do you really have that or did you mistype it? Are they executable?

---

### Post by registerme on 2008-09-05
> **Vivaldi Gloria said:**
> It works for me when the following are in the same folder:

```
#!/bin/bash
./s2.sh somearg
```

```
#!/bin/bash
echo $1
```

The first is named s1.sh and the second one is s2.sh.

```
vivaldi@narval:~/test$ ./s1.sh
somearg
```

In your s1.sh above you've a dot-space-dot. Do you really have that or did you mistype it? Are they executable?

If you are using bash, it works, as is mentioned by another post above. My question is, why sh/dash does not work? Is it a bug?

'. ./s2.sh' is not a typo, it means the calling shell program will retain the environment changed by the child program. In this case it really does not matter, without the dot, it should be the same.

---

### Post by Vivaldi Gloria on 2008-09-05
> **registerme said:**
> If you are using bash, it works, as is mentioned by another post above. My question is, why sh/dash does not work? Is it a bug?

Sorry. Don't know much about dash. It lacks some features of bash. For example I know that pushd popd is not available in dash. But I have no idea why your script doesn't work. 

Write #!/bin/bash and be happy. ;)

> '. ./s2.sh' is not a typo, it means the calling shell program will retain the environment changed by the child program. 

Thanks. Didn't know that.

---

