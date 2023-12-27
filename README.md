# Memo

GitHub 파일을 VS CODE테마로 웹에서 보기<br>
github.com -> github1s.com로 변경하면됨<br>

https://github.com/pixelani/works/blob/main/incrude.html<br>
https://github1s.com/pixelani/works/blob/main/incrude.html<br>

# Html Include

<pre>

  <!DOCTYPE html>
<html>
<script>
function includeHTML() {
  var z, i, elmnt, file, xhttp;
  /*loop through a collection of all HTML elements:*/
  z = document.getElementsByTagName("*");
  for (i = 0; i < z.length; i++) {
    elmnt = z[i];
    /*search for elements with a certain atrribute:*/
    file = elmnt.getAttribute("w3-include-html");
    if (file) {
      /*make an HTTP request using the attribute value as the file name:*/
      xhttp = new XMLHttpRequest();
      xhttp.onreadystatechange = function() {
        if (this.readyState == 4) {
          if (this.status == 200) {elmnt.innerHTML = this.responseText;}
          if (this.status == 404) {elmnt.innerHTML = "Page not found.";}
          /*remove the attribute, and call this function once more:*/
          elmnt.removeAttribute("w3-include-html");
          includeHTML();
        }
      }      
      xhttp.open("GET", file, true);
      xhttp.send();
      /*exit the function:*/
      return;
    }
  }
};
</script>
<body>

<div w3-include-html="h1.html"></div> 
<div w3-include-html="content.html"></div> 

<script>
includeHTML();
</script>

</body>
</html>

  
</pre>
