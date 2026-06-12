---
title: "Best way to send emails using php/perl?"
date: 2008-11-27
forum: General Help
---

### Post by jenmo917 on 2008-11-27
Hello,

I have a mysql database-table with emails and i want to send mails
to them, how do i do this the best way from a php/perl? script?

I have a SMTP server running and working on Ubuntu 8.10.

Could this be something?

<?PHP
$query="SELECT email from `email-table`;

$result=mysql_query($query);


while($row=mysql_fetch_assoc($result))

{


     $to = $row['email'];
     $subject = "Hi!";
     $body = "Hi,\n\nHow are you?";
     if (mail($to, $subject, $body)) {
         echo("<p>Message successfully sent!</p>");
     }
     else {
     echo("<p>Message delivery failed...</p>");
     }
}
?>

thanks, jm.

---

