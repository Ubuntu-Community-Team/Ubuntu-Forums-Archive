---
title: "Batch file"
date: 2008-08-11
forum: General Help
---

### Post by hidarikani on 2008-08-11
Every day I have to copy a .source/folder to .destination/
How do I create an application launcher that performs this action?

---

### Post by jimv on 2008-08-11
It's called a shell script.  Create a new file and put this in it:

```

#!/bin/bash

cp /somefile /somewhere
```

Then run this command to make it executable:

```
chmod +x yourscript
```

---

