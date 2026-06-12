---
title: "sed command help"
date: 2008-07-26
forum: General Help
---

### Post by Ohs0Ahxi on 2008-07-26
I've managed to figure out or find on google most of the sed and awk commands ive needed, But i cant figure out how to add "," to the end of the last line of a file. 
At the moment i use 
```
sed -i '$a\,'
``` which adds a "," on a new line at the end of the file. But i dont know how to add to the existing last line. 

Any help appreciated

* EDIT *
```
sed -i '$s/$/&,/' FILE
```

---

### Post by ghostdog74 on 2008-07-26
no need to use sed, just echo
```

echo "," >> file


```

---

