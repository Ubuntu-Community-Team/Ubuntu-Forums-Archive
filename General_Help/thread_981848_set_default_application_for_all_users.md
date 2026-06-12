---
title: "set default application for all users"
date: 2008-11-14
forum: General Help
---

### Post by tariqf on 2008-11-14
Hi how can I set a default application for all users on my Ubuntu 8.10 machine? Specifically I have installed acroread and I want this as the default PDF reader for all my users without having to log onto each one.

Thanks

---

### Post by geirha on 2008-11-14
Do the change on your user, then look at the file ~/.local/share/applications/mimeapps.list. You should see an entry like this:
```

application/pdf=AdobeReader.desktop;

```

To make that global, create a similar file in /usr/share/applications/, there's likely no such file there already (there's none by default), so you can create a new one with a command like this: (This will overwrite the file if it's already there, so check first!)
```
echo -e '[Added Associations]\napplication/pdf=AdobeReader.desktop;' | sudo tee /usr/share/applications/mimeapps.list
```

If mimapps.list is already there, you can just append the new association
```
echo 'application/pdf=AdobeReader.desktop;' | sudo tee --append /usr/share/applications/mimeapps.list
```

---

