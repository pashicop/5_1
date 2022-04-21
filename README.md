# 5_1
# 1
При полной аппаратной виртуализации гипервизор являет собой хостовую операционную систему, которая позволяет создавать, управлять, удалять виртуальные машины с любой гостевой ОС, при этом выделением ресурсов хоста занимается гипервизор. Используют для долгосрочной полноценной работы гостевых ВМ
При паравиртуализации гипервизор запускается на хостовой ОС как приложение и позволяет запускать ВМ, изменяя ядро для взаимодействия с ресурсами хоста. Удобно использовать для быстрого создания ВМ на не специально выделенной под виртуализацию машине.
При виртуализации на уровне ОС ВМ запускаются как изолированные процессы хостовой ОС. Очень удобно для тестирования продуктов в разработке приложений, сервисов.  
# 2
Высоконагруженная база данных, чувствительная к отказу – на физический сервер. Меньше рисков отказа из-за отсутствия гипервизоров и виртуализации. Но можно и паравиртуализацию с кластеризацией  
Различные web-приложения – паравиртуализация, виртуализация уровня ОС в зависимости от нагрузки. Обеспечит лучшую утилизацию серверов.
Windows системы для использования бухгалтерским отделом - физический сервер, если это для системы, требующей большое количество ресурсов или паравиртуализация на hyper-V, т.к. хорошо поддерживается
Системы, выполняющие высокопроизводительные расчеты на GPU - физический сервер, т.к. можно получить наиболюшую производительность
# 3
100 виртуальных машин на базе Linux и Windows, общие задачи, нет особых требований. Преимущественно Windows based инфраструктура, требуется реализация программных балансировщиков нагрузки, репликации данных и автоматизированного механизма создания резервных копий.
Hyper-V или VMWare vSphere
Требуется наиболее производительное бесплатное open source решение для виртуализации небольшой (20-30 серверов) инфраструктуры на базе Linux и Windows виртуальных машин.
Xen-серверы, 
Необходимо бесплатное, максимально совместимое и производительное решение для виртуализации Windows инфраструктуры.
Hyper-V
Необходимо рабочее окружение для тестирования программного продукта на нескольких дистрибутивах Linux.
KVM, docker
# 4
Гетерогенная структура требует более квалифицированных инженеров для поддержки или увеличивает их число -> Стоимость обслуживания системы увеличивается. Также может возникнуть ситуация, когда единственный специалист по одной из структур заболел, уволился и тп, тогда систему некому поддерживать. 
Может возникнуть ситуация, когда одна структура виртуализации сильно загружена, а другая очень слабо. При этом мы не можем выравнять нагрузку из-за разных систем, т.к. это могло бы быть при гомогенной структуре. 
Неэффективная утилизация при кластеризации.
Для минимизации рисков и проблем нужно обучать персонал управлению разными структурами, постоянно следить за распределением нагрузки между структурами и переносить ВМ для балансировки нагрузки.
В обычном офисе без отдела разработки собственных приложений, сервисов, я бы создавал гомогенную структуру виртуализации, например, на vSphere. Но если есть такой отдел,  то для них можно отдельно выделить физические сервера под развёртывание тестовых сред на KVM или других системах.
