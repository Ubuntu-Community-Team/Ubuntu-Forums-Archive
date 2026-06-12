---
title: "help with  cut, and a bash script"
date: 2008-11-30
forum: General Help
---

### Post by markp1989 on 2008-11-30
im in the middle of writing a scrips that will pull data from my torrent slave, and then i will display it in my conky 


```
#!/bin/bash
host=10.0.0.99/torrentflux
user=******
pass=******
curl -c tf_cookie -d username=$user -d iamhim=$pass $host/login.php >> /dev/null

echo `curl -H "Expect:" -b tf_cookie $host/index.php | grep -i '<strong>' | cut -c42-44` |  cut -c9-12 #download speed 
echo `curl -H "Expect:" -b tf_cookie $host/index.php | grep -i '<strong>' | cut -c42-44` |  cut -c13-16 #upload speed 
echo `curl -H "Expect:" -b tf_cookie $host/index.php | grep -i '<strong>' | cut -c42-44` |  cut -c17-22 #download speed 

```

here is the output
```
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
101  1937  100  1910    0    27  14096    199 --:--:-- --:--:-- --:--:-- 15823
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 22623    0 22623    0     0  51225      0 --:--:-- --:--:-- --:--:--  250k
0.1     **<--- download speed**
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 22623    0 22623    0     0  50797      0 --:--:-- --:--:-- --:--:--  230k
0.0  **<--- upload speed**
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 22623    0 22623    0     0  50792      0 --:--:-- --:--:-- --:--:--  241k
279 **<--- free space**
[mark@markspc Desktop]$ 
 
```


what i wana do is have the output say
down : NN kbs
up   : NN kbs
free : NN gb 

any help will be apriciated

EDIT: just checked the output chanes  , and the cuts dont work if i add or remove  torrents

---

