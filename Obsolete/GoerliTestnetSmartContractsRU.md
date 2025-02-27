# Goerli Тестнет Смарт Контракты для поставщиков капитала в Morpheus

## Введение

Чтобы принять участие в тестировании Goerli Смарт Контрактов для поставщиков ликвидности в Morpheus, необходимо пройти три этапа:
1) Получить goETH (если у вас его еще нет)
2) Конвертировать goETH в Goerli stETH 
3) Подключиться и провзаимодействовать со Смарт Контрактом 

## Адреса Смарт Контрактов
- Токен MOR: 0x454AE850eE61a98BF16FABA3a73fb0dD02D75C40 
- Ссылка на код Смарт Контракта: https://goerli.etherscan.io/address/0x454AE850eE61a98BF16FABA3a73fb0dD02D75C40#code

- Распределение наград: 0x850A65DA677264bbb7536f8446336C022eCc85Dc
- Ссылка на код Смарт Контракта: https://goerli.etherscan.io/address/0x850A65DA677264bbb7536f8446336C022eCc85Dc#code

- Токен stETH: [0xae7ab96520DE3A18E5e111B5EaAb095312D7fE84](https://goerli.etherscan.io/address/0x1643e812ae58766192cf7d2cf9567df2c37e9b7f) 

## Часть 1: Получение goETH
- Для начала, у вас должен быть установлен Metamask или другой web3 кошелек, который вам удобен. Вам нужно перейти к настройкам сети, которые по умолчанию обычно установлены на Ethereum, затем выбрать тестовую сеть Goerli или добавить ее вручную. 

- Следующим шагом является получение goETH для вашего адреса. Для этого вы можете использовать сайты-краны, например, https://goerli-faucet.pk910.de/#/

- Есть много других кранов для тестовой сети Goerli, которые легко можно найти, но для них обычно требуется адрес, который был активен в основной сети Ethereum.

## Часть 2: Конвертирование goETH в stETH 

-  Затем вам нужно конвертировать свой goETH в Goerli stETH. Вы можете сделать это на сайте https://stake.testnet.fi/. (Примечание: На сайте может быть достигнут лимит конвертирования stETH, в этом случае, воспользуйтесь следующим способом) 

- Еще один способ получения stETH, это обмен на [Uniswap.](https://app.uniswap.org/swap?outputCurrency=0x1643E812aE58766192Cf7D2Cf9567dF2C37e9B7F&chain=goerli) 

## Часть 3: Взаимодействие со Смарт Контрактом 

- Процесс состоит из несколько этапов. Сначала мы подключимся и дадим доступ контракту, а затем внесем в него stETH. Позже мы рассмотрим, как получить награды и снять stETH.  

## Подключение к контракту
Чтобы взаимодействовать с контрактом, необходимо открыть его в обозревателе блоков по [ссылке](https://goerli.etherscan.io/address/0x850A65DA677264bbb7536f8446336C022eCc85Dc#code) и перейди к вкладке "Read as Proxy" или "Write as Proxy" и подключить ваш кошелек ![SmartContractExample1](https://github.com/MorpheusAIs/Morpheus/assets/1563345/739127b8-0a44-4112-94d9-2670442b9c09)
На изображении выше мы переходим во вкладку "Write as Proxy" и нажимаем на кнопку "Connect to Web3" чтобы подключить наш кошелек. Об удачном подключении вы узнаете когда красный индикатор станет зеленым. Убедитесь, что подключенный адрес тот самый, который вы используете в кошельке. 

## Предоставление разрешения контракту
- Перед внесением stETH, контракту необходимо предоставить разрешение на то, что он сможет отправить stETH с вашего кошелька. 
- Пример: https://goerli.etherscan.io/address/0x1643E812aE58766192Cf7D2Cf9567dF2C37e9B7F#writeProxyContract
![exampleofapprove](https://github.com/MorpheusAIs/Morpheus/assets/1563345/d51a84da-9f38-42a7-9fb4-2f9dd2edfcff)

- Вам будет необходимо указать сумму stETH, которую вы хотите отправить в поле `_amount (uint256)`, и указать ее в WEI, а не ETH. Для этого, вы можете воспользоваться калькулятором https://eth-converter.com. Например, если вы хотите отправить 0.01 stETH, то это будет 10000000000000000 WEI. В поле `_spender (address)` вам необходимо внести адрес Смарт Контракта 0x850A65DA677264bbb7536f8446336C022eCc85Dc и потом нажать Write и подтвердить транзакцию.

## Внесение средств (стейкинг)
- Внесение средств проводится в пулы. 
- Вам необходимо указать сумму stETH, которую вы хотите внести (не менее чем та, на которую вы дали разрешение в предудущем шаге).
- Также необходимо указать ID пула, для тестирования мы будем использовать "0"
- Пример: https://goerli.etherscan.io/address/0x850A65DA677264bbb7536f8446336C022eCc85Dc#code
![SmartContractExample2](https://github.com/jabo38/morpheus-images/assets/10395907/b47c571b-e858-4c19-b73a-8ca8ef4acf8d) 

- Как и в предыдущем этапе, вам будет необходимо указать сумму в поле `_amount (uint256)`, и указать ее в WEI, а не ETH. Для этого, вы можете воспользоваться калькулятором https://eth-converter.com. Например, если вы хотите отправить 0.01 stETH (минимальная сумма), то это будет 10000000000000000 WEI.
- В поле с указанием номера пула `poolId_ (uint256)` введите "0", нажмите "Write" и подтвердите транзакцию.
- В случае, если вы захотите внести больше средств, вам будет необходимо повторить последние два шага, а именно, дать разрещение контракту и внести средства.

## Как получить награды?
- После внесения средств (стейкинга), должно пройти определенное время, для того, чтобы контракт начислил вам токены MOR.
- Вам необходимо вызвать функцию снятия вознаграждений в Смарт Контракте.
- Необходимо указать номер пула и адрес вашего кошелька
![SmartContractExample5](https://github.com/jabo38/morpheus-images/assets/10395907/eeb443a5-d28a-460e-9fd0-477dcc663789)

- Убедитесь в том, что ваш кошелек подключен (зеленый индикатор), затем введите "0" в поле `poolId_ (uint256)`, укажите ваш адрес в поле `_user (address)` и нажмите "Write".

## Как снять stETH со Смарт Контракта?
- Вы можете снять всю сумму или только часть.
- Необходимо указать номер пула и сумму для снятия.
- На ваш адрес также автоматически будут зачислены все награды в токене MOR доступные на момент снятия.
![SmartContractExample6](https://github.com/jabo38/morpheus-images/assets/10395907/579b7d74-8526-45de-a531-2df4c965c12a)

- В секции 13, вам необходимо ввести "0" в поле `poolId_ (uint256)` и сумму, которую вы хотите снять, в поле `_amount (uint256)`. Сумму необходимо ввести в WEI, так что в случае необходимости, воспользуйтесь https://eth-converter.com для конвертации.

Если возникнут дополнительные вопросы, вы можете их задать в 

Телеграмм https://t.me/MorpheusAI 

Дискорд https://discord.gg/YEhvSNmp 
