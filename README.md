```javascript
 //List following
    if (document.getElementById('userFollowing')) {
      document.getElementById('userFollowing').addEventListener('click', async function () {

        showLoadingPopup()
        try {
          await fetch('http://127.0.0.1:8000/sanctum/csrf-cookie', {
            credentials: 'include'
          });
          const csrfToken = decodeURIComponent(getCookie('XSRF-TOKEN'));

          const response = await fetch(`${apiUrl}/user/listFollowing`, {
            method: 'GET',
            credentials: 'include',        // ← send the session cookie
            headers: {
              'Content-Type': 'application/json',
              'Accept': 'application/json',
              'X-XSRF-TOKEN': csrfToken
            },
          });

          const data = await response.json();

          if (response.ok) {
            console.log(data)
            showSuccessPopup()
          } else {
            document.getElementById('message').innerText = `${data.message}: ${data.error}` || 'An unknown error occurred';
            showErrorPopup()
          }
        } catch (error) {
          document.getElementById('message').innerText = error.message || 'An unknown error occurred';
          showErrorPopup()
        }
        finally {
          hideLoadingPopup()
        }

      })
    }
```




```javascript
     //List followers
     if (document.getElementById('userFollowers')) {
      document.getElementById('userFollowers').addEventListener('click', async function () {

        showLoadingPopup()
        try {
          await fetch('http://127.0.0.1:8000/sanctum/csrf-cookie', {
            credentials: 'include'
          });
          const csrfToken = decodeURIComponent(getCookie('XSRF-TOKEN'));

          const response = await fetch(`${apiUrl}/user/listFollowers`, {
            method: 'GET',
            credentials: 'include',        // ← send the session cookie
            headers: {
              'Content-Type': 'application/json',
              'Accept': 'application/json',
              'X-XSRF-TOKEN': csrfToken
            },
          });

          const data = await response.json();

          if (response.ok) {
            console.log(data)
            showSuccessPopup()
          } else {
            document.getElementById('message').innerText = `${data.message}: ${data.error}` || 'An unknown error occurred';
            showErrorPopup()
          }
        } catch (error) {
          document.getElementById('message').innerText = error.message || 'An unknown error occurred';
          showErrorPopup()
        }
        finally {
          hideLoadingPopup()
        }

      })
    }
```
