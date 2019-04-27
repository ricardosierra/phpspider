# phpspider -- Crawler em PHP                                                           
=============                                                                                                                                                                                    
                                                                                                                                                                                                 
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/ricardosierra/phpspider/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/ricardosierra/phpspider/?branch=master)         
[![Code Coverage](https://scrutinizer-ci.com/g/ricardosierra/phpspider/badges/coverage.png?b=master)](https://scrutinizer-ci.com/g/ricardosierra/phpspider/?branch=master)                         
                                                                                                                                                                                                 
[![Latest Stable Version](https://poser.pugx.org/ricardosierra/phpspider/v/stable.png)](https://packagist.org/packages/ricardosierra/phpspider)                                                    
[![Total Downloads](https://poser.pugx.org/ricardosierra/phpspider/downloads.png)](https://packagist.org/packages/ricardosierra/phpspider)                                                         
[![Latest Unstable Version](https://poser.pugx.org/ricardosierra/phpspider/v/unstable.png)](https://packagist.org/packages/ricardosierra/phpspider)                                                
[![License](https://poser.pugx.org/ricardosierra/phpspider/license.png)](https://packagist.org/packages/ricardosierra/phpspider)

"Usei o rastreador para" roubar "um programa que conhece cerca de um milhão de usuários, apenas para provar que o PHP é a melhor linguagem do mundo."

O Phpspider é um framework de desenvolvimento de rastreador. Com essa estrutura, você não precisa entender a implementação técnica subjacente dos rastreadores, os rastreadores são bloqueados por sites e alguns sites exigem reconhecimento de código de login ou verificação para rastrear. Com algumas linhas de código PHP, você pode criar seu próprio rastreador, usando a biblioteca de classes Worker multiprocessada empacotada pela estrutura, o código é mais conciso, a eficiência de execução é mais rápida e mais rápida.

Existem algumas regras de rastreamento para sites específicos no diretório de demonstração, desde que você instale o ambiente PHP, o código pode ser executado diretamente a partir da linha de comando. Desenvolvedores interessados em rastreadores podem se juntar ao grupo QQ para discutir: 147824717.

## Requirements:

 * PHP 7.0+
 * Composer

## Installation

 You can install this library via Composer: `composer require ricardosierra/phpspider` 

## Examples

Vamos dar uma anedota como exemplo para ver como é o nosso réptil:

```
$configs = array(
    'name' => 'Anedota',
    'domains' => array(
        'qiushibaike.com',
        'www.qiushibaike.com'
    ),
    'scan_urls' => array(
        'http://www.qiushibaike.com/'
    ),
    'content_url_regexes' => array(
        "http://www.qiushibaike.com/article/\d+"
    ),
    'list_url_regexes' => array(
        "http://www.qiushibaike.com/8hr/page/\d+\?s=\d+"
    ),
    'fields' => array(
        array(
            // Extraia o conteúdo do artigo na página de conteúdo
            'name' => "article_content",
            'selector' => "//*[@id='single-next-link']",
            'required' => true
        ),
        array(
            // Autor do artigo que extraiu a página de conteúdo
            'name' => "article_author",
            'selector' => "//div[contains(@class,'author')]//h2",
            'required' => true
        ),
    ),
);
$spider = new phpspider($configs);
$spider->start();
```
A estrutura geral do rastreador é assim: Primeiro, defina uma matriz $ configs, que define algumas informações sobre o site a ser rastreado e, em seguida, chama-o.```$spider = new phpspider($configs);```E```$spider->start();```Para configurar e iniciar o rastreador.

#### A interface em execução é a seguinte: 

![](http://www.epooll.com/zhihu/pachong.gif)

Para mais detalhes, siga para:

[Documento de desenvolvimento](http://doc.phpspider.org)


## Contributing

For contributing guidelines, please see [CONTRIBUTING.md](CONTRIBUTING.md)

## Credits

- Seatle Yang