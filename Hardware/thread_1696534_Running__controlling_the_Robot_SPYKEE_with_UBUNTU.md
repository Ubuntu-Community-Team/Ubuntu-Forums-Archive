---
title: "Running / controlling the Robot SPYKEE with UBUNTU ?"
date: 2011-02-27
forum: Hardware
---

### Post by honeybear on 2011-02-27
Hello,

I found that some users have made this, or in development.

[http://spykee.duskofsolace.com/index.php?title=Main_Page](http://spykee.duskofsolace.com/index.php?title=Main_Page)

Has someone a DEB to try the program to control the robot from Ubuntu? 

Thanks in advance!

---

### Post by honeybear on 2011-02-27
I try distant over internet + router port forwarded

perl -w controlspykee.perl

```
#!/usr/bin/perl

$host = "XX.X.XXX.XX";
$port = 11000;
# I forwarded the port 11000 on the router to the IP of spykee !!!
$username = "admin";
$password = "ubuntu";

########################

use IO::Socket;

$ulen = length($username);
$plen = length($password);
$tlen = ($ulen + $plen + 2);

$socket = new IO::Socket::INET (PeerAddr=>$host,PeerPort=>$port,Proto=>'tcp') or die "Couldn't connect to Servern";
$socket->autoflush(1);

print $socket "PK", chr(10), chr(0), chr($tlen), chr($ulen), $username, chr($plen), $password;
sleep 2;
print $socket "PK", chr(4), chr(0), chr(2), chr(0), chr(1);
sleep 3;

open(FH, ">", "spykee.jpg");
print $socket "PK", chr(15), chr(0), chr(2), chr(1), chr(1);
print $socket "PK", chr(15), chr(0), chr(2), chr(2), chr(1);

while (1) {
  $socket->recv($recv_data,1);
  $rh = unpack("H*", $recv_data);

  if ($rec == 1) {
    print FH "$recv_data";
    if ($count == $size) {
      close(FH);
      exit(0);
    }
    $count++;
  } elsif (($ah == "50") && ($bh == "4b") && ($ch == "02") && ($rec != 1)) {
    if ($zh) {
      $yh = $zh;
      $zh = $rh;
    }
    if ($yh) {
      $rec = 1;
      $count = 1;
      $tmp = $yh . $zh;
      $size = hex($tmp);
      print "size: $yh $zh ($size)n";
    }
    $zh = $rh;
  } else {
    $ah = $bh;
    $bh = $ch;
    $ch = $rh;
  }
}

#_EOF_


```



[COLOR="Red"]but not working :( [/COLOR]

---

