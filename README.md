# О проекте

В этом проекте реализованы возможности фулл-стак приложения на основе .NET(Xamarin) и React framework, с исползованием web3. В качестве демонстрации был выбран проект платформа для голосования, с использованием регистрации каждого действия в сети блокчейн.
В основе бэкенда данный проект представляет собой шаблон SDK на основе Xamarin. SDK - это набор инструментов и библиотек, который позволяет разработчикам создавать приложения и решения на определенной платформе.
Xamarin - это платформа для разработки мобильных приложений, которая использует язык программирования C# и позволяет создавать приложения для операционных систем Android и iOS. В данном проекте используется Xamarin для разработки SDK, который может быть использован другими разработчиками для создания мобильных приложений на платформах Android и iOS.
​Для бэкенда существует реализация функций свойств, благодаря которым работает API для принятия хэшей каждой произведенной транзакцией, дополнительно проект был скомпилироан и собран для Android/IOS, а также протестирован на дополнительных версий систем.

​Для фронтенда был выбран React, с помощью дополнительных библиотек была реализована логика приложения, позволяет сохранять голоса пользователя на основе его кошелька MetaMask.
Данный фреймворк был выбран для общего понимания, и упрощения хостинга сайта в сети IPFS.
 
## Как использовать

Для использования SDK на основе Xamarin необходимо скачать и установить Xamarin на ваш компьютер. Затем, можно создать новый проект на основе шаблона SDK и начать разрабатывать свое приложение, используя функционал, предоставляемый в SDK.
Пример использования SDK в проекте Xamarin можно увидеть на следующем коде:

# Copy code

```
using Xamarin.SDK;

SDK.Init("YOUR_APP_KEY");

SDK.DoSomething();

```

# Internal usage

```
public virtual async Task<string> SendRequestAsync(string methodParameters, string id, string url)
        {
            if (Account == null) throw new InvalidOperationException("Account has not been set to send the request");
            var transactionInput = JsonConvert.DeserializeObject<TransactionInput>(methodParameters);
            var validRequest = true;
            if (ValidateRequest != null) validRequest = await ValidateRequest(transactionInput);

            if (validRequest)
            {
                var web3 = new Nethereum.Web3.Web3(Account, url);
                var txn = await web3.TransactionManager.SendTransactionAsync(transactionInput);
                return GetResponseString(txn, id);
            }
            else
            {
                return Scripts.GetResponseError("Rejected transaction");
            }
        }
```

# Frontend

Запуск сборки с помощью

```
npm install && npm start 
```

# Software 
VS15, Xamarin WebView, NodeJS, npm, MetaMaskm, IPFS(fleek)
