---
title: "[SOLVED] &amp;quot;sh&amp;quot; vs &amp;quot;./&amp;quot;"
date: 2008-10-04
forum: General Help
---

### Post by lost09 on 2008-10-04
Greetings all,

I have a script named make_page which successfully runs with the command "sh", but refuses to run with "./". Can anyone explain why this is (i.e. the difference between these two commands)? I have never had difficulty executing scripts with "./" before, and am both frustrated and confused.

Thanks,
l

---

### Post by lswb on 2008-10-04
To run with ./script, the script must be executable

chmod +x script

and the first line of the script must indicate what program will be used to run it, e.g. for a bash script , the first line would be:

#!/bin/bash

---

### Post by lost09 on 2008-10-05
Ah, I had accidentally (and unknowingly) deleted #!/bin/bash. Thanks!

I don't suppose you can tell me why "sh script" worked even without #!/bin/bash?

---

### Post by gausie on 2008-10-05
#!/bin/bash usually says what the file is suppose to run with.

Since you ran it by passing it to sh, theres no need for it!

Gausie

---

### Post by lost09 on 2008-10-09
Ah, that makes excellent sense. Thanks!

---

